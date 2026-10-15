# tcphdr

## Overview

## Summary

### Member variables

| Name | Description |
| -- | -- |
| \_\_extension\_\_
	union { struct {

	uint16_t source;
	uint16_t dest;
	uint32_t seq;
	uint32_t ack_seq;
	uint16_t res1:4;
	uint16_t doff:4;
	uint16_t fin:1;
	uint16_t syn:1;
	uint16_t rst:1;
	uint16_t psh:1;
	uint16_t ack:1;
	uint16_t urg:1;
	uint16_t res2:2;
	uint16_t doff:4;
	uint16_t res1:4;
	uint16_t res2:2;
	uint16_t urg:1;
	uint16_t ack:1;
	uint16_t psh:1;
	uint16_t rst:1;
	uint16_t syn:1;
	uint16_t fin:1;
	uint16_t window;
	uint16_t check;
	uint16_t urg_ptr;

	}; struct {

	uint16_t th_sport;
	uint16_t th_dport;
	uint32_t th_seq;
	uint32_t th_ack;
	uint8_t th_x2:4;
	uint8_t th_off:4;
	uint8_t th_off:4;
	uint8_t th_x2:4;
	uint8_t th_flags;
	uint16_t th_win;
	uint16_t th_sum;
	uint16_t th_urp;

	}; } |  |


