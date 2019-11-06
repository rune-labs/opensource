Time-Domain Data Ingestion
==========================

```
#
# All timestamps (unless noted otherwse as Medtronic "system ticks") are UNIX
# timestamps as seconds with fraction
#

MEDTRONIC_EPOCH = 951868800   # 2000-03-01 00:00:00 UTC
SYSTEM_TICK_CLOCK = (1 << 16)
SYSTEM_TICK_DURATION = 0.0001
V_UNIT_SCALE = {
    megavolts:  1000000
    kilovolts:  1000
    volts:      1
    millivolts: 0.001
    microvolts: 0.000001
}

medtronic_timestamp_prev = None
n_points_in_packet = None
packet_number_prev = None
sample_rate = None
system_tick_time = 0
system_tick_prev = None
t_chunk_start = None
ticks_per_point = None
timezone_offset = <retrieved from device settings stream>

for packet in record["TimeDomainData"]
    header = packet["Header"]
    channels = packet["ChannelSamples"]
    v_coef = V_UNIT_SCALE[packet["Units"]]

    packet_number = header["dataTypeSequence"]
    medtronic_timestamp = header["timestamp"]["seconds"]
    unix_timestamp = MEDTRONIC_EPOCH + medtronic_timestamp - timezone_offset

    if medtronic_timestamp_prev == None
        # First packet
        medtronic_timestamp_prev = medtronic_timestamp

    if packet["SampleRate"] != sample_rate
        sample_rate = packet["SampleRate"]
        sampling_freq = 250 * (1 << sample_rate)
        sampling_period = 1.0 / sampling_freq
        ticks_per_point = sampling_period / SYSTEM_TICK_DURATION

    if t_chunk_start == None or abs(medtronic_timestamp - medtronic_timestamp_prev) >= 5
        #
        # Too much drift for system tick clock, need to re-sync from MDT
        # timestamp
        #
        t_chunk_start = unix_timestamp
        system_tick_time = 0
        system_tick_prev = header["systemTick"]

    system_tick_end = header["systemTick"]
    ticks_elapsed = (system_tick_end - system_tick_prev) % SYSTEM_TICK_CLOCK
    system_tick_time += ticks_elapsed

    if packet_number_prev == None
        # First packet
        packet_number_prev = packet_number

    n_points_in_packet = length(channels[0]["Value"])
    system_tick_start = system_tick_time - (n_points_in_packet - 1) * ticks_per_point
    ticks_in_packet = n_points_in_packet * ticks_per_point

    t_packet_start = t_chunk_start + (system_tick_start * SYSTEM_TICK_DURATION)

    for i_point in 0..n_points_in_packet
        tick = system_tick_start + (i_point * ticks_per_point)
        t = t_chunk_start + (tick * SYSTEM_TICK_DURATION)

        for i_channel in 0..4
            v = channels[i_channel]["Value"][i_point] * v_coef

            # Output the point to wherever it's stored/used next
            yield (t, i_channel, v)

    system_tick_prev = system_tick_end
    packet_number_prev = packet_number
    medtronic_timestamp_prev = medtronic_timestamp

```
