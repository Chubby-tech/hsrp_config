# HSRP Configuration Guide

## Overview
HSRP (Hot Standby Router Protocol) provides gateway redundancy by allowing multiple routers to share a virtual IP address. One router is active while others remain standby.

## Topology Example
- R1: 192.168.1.1 (Active preferred)
- R2: 192.168.1.2 (Standby)
- Virtual IP: 192.168.1.254

## R1 Configuration
interface g0/0
 ip address 192.168.1.1 255.255.255.0
 standby 1 ip 192.168.1.254
 standby 1 priority 110
 standby 1 preempt

## R2 Configuration
interface g0/0
 ip address 192.168.1.2 255.255.255.0
 standby 1 ip 192.168.1.254
 standby 1 priority 100
 standby 1 preempt

## Verification
show standby

## Key Points
- Virtual IP is used as default gateway
- Preempt allows higher priority router to regain active role
- Failover is automatic
