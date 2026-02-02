# Dual-isp-bgp-inbound-routing
To simulate a Dual ISP BGP environment where inbount traffic should prefer ISP1(Primary) and use ISP2 only as backup.

# Problem Statement
Inbound traffic for Customer network 172.16.1.1/32
is preferring ISP2 instead of ISP1.

Design intent:
ISP1 should be primary
ISP2 should be backup.

# Observations
- Customer is multihomed with ISP1 (AS100) and ISP2 (AS200)
- Customer AS is 65001
3 Prefix is advertised normally to both ISPs
4 No AS-path prepending is configured

# Commands used
show ip bgp
show ip bgp summary

# Command Output Analysis
ISP1 sees AS-path: 65001
ISP2 sees AS-path: 65001

AS-path length is equal,
so upstream networks may choose ISP2
based on shortest internal path.

# Root Cause
Inbound traffic is controlled by external networks.

Since AS-path length via ISP2
is not longer than ISP1,
traffic prefers ISP2.


