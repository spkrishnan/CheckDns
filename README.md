# CheckDNS

The goal of this script is to query a DNS server and remove a specific route if the DNS server is not responding to the query

- The event options runs the script every minute
- The script queries the DNS server
- If there is no response from the DNS server, the route specified in the script is removed from the configuration


Copy the script to “/var/db/scripts/event” directory on the switch.

Here is the configuration required on the switch to run it.
- set event-options generate-event CHECK_DNS_EVENT time-interval 60
- set event-options policy CHECKDNSSTATUS events CHECK_DNS_EVENT
- set event-options policy CHECKDNSSTATUS then event-script checkdns.slax
- set event-options event-script file checkdns.slax

