# tcp_info

## Overview

<!--Device-struct tcp_info {...}--><!--Device-struct tcp_info {...}-End-->

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t tcpi_state | <!--Device-uint8_t tcpi_state--><!--Device-uint8_t tcpi_state-End--> |
| uint8_t tcpi_ca_state | <!--Device-uint8_t tcpi_ca_state--><!--Device-uint8_t tcpi_ca_state-End--> |
| uint8_t tcpi_retransmits | <!--Device-uint8_t tcpi_retransmits--><!--Device-uint8_t tcpi_retransmits-End--> |
| uint8_t tcpi_probes | <!--Device-uint8_t tcpi_probes--><!--Device-uint8_t tcpi_probes-End--> |
| uint8_t tcpi_backoff | <!--Device-uint8_t tcpi_backoff--><!--Device-uint8_t tcpi_backoff-End--> |
| uint8_t tcpi_options | <!--Device-uint8_t tcpi_options--><!--Device-uint8_t tcpi_options-End--> |
| uint8_t tcpi_snd_wscale : 4, tcpi_rcv_wscale : 4 | <!--Device-uint8_t tcpi_snd_wscale : 4, tcpi_rcv_wscale : 4--><!--Device-uint8_t tcpi_snd_wscale : 4, tcpi_rcv_wscale : 4-End--> |
| uint8_t tcpi_delivery_rate_app_limited : 1 | <!--Device-uint8_t tcpi_delivery_rate_app_limited : 1--><!--Device-uint8_t tcpi_delivery_rate_app_limited : 1-End--> |
| uint32_t tcpi_rto | <!--Device-uint32_t tcpi_rto--><!--Device-uint32_t tcpi_rto-End--> |
| uint32_t tcpi_ato | <!--Device-uint32_t tcpi_ato--><!--Device-uint32_t tcpi_ato-End--> |
| uint32_t tcpi_snd_mss | <!--Device-uint32_t tcpi_snd_mss--><!--Device-uint32_t tcpi_snd_mss-End--> |
| uint32_t tcpi_rcv_mss | <!--Device-uint32_t tcpi_rcv_mss--><!--Device-uint32_t tcpi_rcv_mss-End--> |
| uint32_t tcpi_unacked | <!--Device-uint32_t tcpi_unacked--><!--Device-uint32_t tcpi_unacked-End--> |
| uint32_t tcpi_sacked | <!--Device-uint32_t tcpi_sacked--><!--Device-uint32_t tcpi_sacked-End--> |
| uint32_t tcpi_lost | <!--Device-uint32_t tcpi_lost--><!--Device-uint32_t tcpi_lost-End--> |
| uint32_t tcpi_retrans | <!--Device-uint32_t tcpi_retrans--><!--Device-uint32_t tcpi_retrans-End--> |
| uint32_t tcpi_fackets | <!--Device-uint32_t tcpi_fackets--><!--Device-uint32_t tcpi_fackets-End--> |
| uint32_t tcpi_last_data_sent | <!--Device-uint32_t tcpi_last_data_sent--><!--Device-uint32_t tcpi_last_data_sent-End--> |
| uint32_t tcpi_last_ack_sent | <!--Device-uint32_t tcpi_last_ack_sent--><!--Device-uint32_t tcpi_last_ack_sent-End--> |
| uint32_t tcpi_last_data_recv | <!--Device-uint32_t tcpi_last_data_recv--><!--Device-uint32_t tcpi_last_data_recv-End--> |
| uint32_t tcpi_last_ack_recv | <!--Device-uint32_t tcpi_last_ack_recv--><!--Device-uint32_t tcpi_last_ack_recv-End--> |
| uint32_t tcpi_pmtu | <!--Device-uint32_t tcpi_pmtu--><!--Device-uint32_t tcpi_pmtu-End--> |
| uint32_t tcpi_rcv_ssthresh | <!--Device-uint32_t tcpi_rcv_ssthresh--><!--Device-uint32_t tcpi_rcv_ssthresh-End--> |
| uint32_t tcpi_rtt | <!--Device-uint32_t tcpi_rtt--><!--Device-uint32_t tcpi_rtt-End--> |
| uint32_t tcpi_rttvar | <!--Device-uint32_t tcpi_rttvar--><!--Device-uint32_t tcpi_rttvar-End--> |
| uint32_t tcpi_snd_ssthresh | <!--Device-uint32_t tcpi_snd_ssthresh--><!--Device-uint32_t tcpi_snd_ssthresh-End--> |
| uint32_t tcpi_snd_cwnd | <!--Device-uint32_t tcpi_snd_cwnd--><!--Device-uint32_t tcpi_snd_cwnd-End--> |
| uint32_t tcpi_advmss | <!--Device-uint32_t tcpi_advmss--><!--Device-uint32_t tcpi_advmss-End--> |
| uint32_t tcpi_reordering | <!--Device-uint32_t tcpi_reordering--><!--Device-uint32_t tcpi_reordering-End--> |
| uint32_t tcpi_rcv_rtt | <!--Device-uint32_t tcpi_rcv_rtt--><!--Device-uint32_t tcpi_rcv_rtt-End--> |
| uint32_t tcpi_rcv_space | <!--Device-uint32_t tcpi_rcv_space--><!--Device-uint32_t tcpi_rcv_space-End--> |
| uint32_t tcpi_total_retrans | <!--Device-uint32_t tcpi_total_retrans--><!--Device-uint32_t tcpi_total_retrans-End--> |
| uint64_t tcpi_pacing_rate | <!--Device-uint64_t tcpi_pacing_rate--><!--Device-uint64_t tcpi_pacing_rate-End--> |
| uint64_t tcpi_max_pacing_rate | <!--Device-uint64_t tcpi_max_pacing_rate--><!--Device-uint64_t tcpi_max_pacing_rate-End--> |
| uint64_t tcpi_bytes_acked | <!--Device-uint64_t tcpi_bytes_acked--><!--Device-uint64_t tcpi_bytes_acked-End--> |
| uint64_t tcpi_bytes_received | <!--Device-uint64_t tcpi_bytes_received--><!--Device-uint64_t tcpi_bytes_received-End--> |
| uint32_t tcpi_segs_out | <!--Device-uint32_t tcpi_segs_out--><!--Device-uint32_t tcpi_segs_out-End--> |
| uint32_t tcpi_segs_in | <!--Device-uint32_t tcpi_segs_in--><!--Device-uint32_t tcpi_segs_in-End--> |
| uint32_t tcpi_notsent_bytes | <!--Device-uint32_t tcpi_notsent_bytes--><!--Device-uint32_t tcpi_notsent_bytes-End--> |
| uint32_t tcpi_min_rtt | <!--Device-uint32_t tcpi_min_rtt--><!--Device-uint32_t tcpi_min_rtt-End--> |
| uint32_t tcpi_data_segs_in | <!--Device-uint32_t tcpi_data_segs_in--><!--Device-uint32_t tcpi_data_segs_in-End--> |
| uint32_t tcpi_data_segs_out | <!--Device-uint32_t tcpi_data_segs_out--><!--Device-uint32_t tcpi_data_segs_out-End--> |
| uint64_t tcpi_delivery_rate | <!--Device-uint64_t tcpi_delivery_rate--><!--Device-uint64_t tcpi_delivery_rate-End--> |
| uint64_t tcpi_busy_time | <!--Device-uint64_t tcpi_busy_time--><!--Device-uint64_t tcpi_busy_time-End--> |
| uint64_t tcpi_rwnd_limited | <!--Device-uint64_t tcpi_rwnd_limited--><!--Device-uint64_t tcpi_rwnd_limited-End--> |
| uint64_t tcpi_sndbuf_limited | <!--Device-uint64_t tcpi_sndbuf_limited--><!--Device-uint64_t tcpi_sndbuf_limited-End--> |
| uint32_t tcpi_delivered | <!--Device-uint32_t tcpi_delivered--><!--Device-uint32_t tcpi_delivered-End--> |
| uint32_t tcpi_delivered_ce | <!--Device-uint32_t tcpi_delivered_ce--><!--Device-uint32_t tcpi_delivered_ce-End--> |
| uint64_t tcpi_bytes_sent | <!--Device-uint64_t tcpi_bytes_sent--><!--Device-uint64_t tcpi_bytes_sent-End--> |
| uint64_t tcpi_bytes_retrans | <!--Device-uint64_t tcpi_bytes_retrans--><!--Device-uint64_t tcpi_bytes_retrans-End--> |
| uint32_t tcpi_dsack_dups | <!--Device-uint32_t tcpi_dsack_dups--><!--Device-uint32_t tcpi_dsack_dups-End--> |
| uint32_t tcpi_reord_seen | <!--Device-uint32_t tcpi_reord_seen--><!--Device-uint32_t tcpi_reord_seen-End--> |
| uint32_t tcpi_rcv_ooopack | <!--Device-uint32_t tcpi_rcv_ooopack--><!--Device-uint32_t tcpi_rcv_ooopack-End--> |
| uint32_t tcpi_snd_wnd | <!--Device-uint32_t tcpi_snd_wnd--><!--Device-uint32_t tcpi_snd_wnd-End--> |


