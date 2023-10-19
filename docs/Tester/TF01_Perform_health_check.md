# Perform Health Checks

Performing regular and timely health checks on an AGW (Access Gateway) is crucial to ensure it is functioning well, free of errors, and to address any emerging problems proactively. These checks should be conducted both before and after making changes to the system to verify that no unintended issues have arisen.

## Connectivity


1. Login to the AGW by running below the command in terminal:

    ```
    ssh magma@<IP of AGW>
    ```
2  Checking Magma interfaces. Make sure eth0 and eth1 are UP.
    ```
    ip addr
    ```

## Enodeb Connection

1. Check S1 and SGi interfaces can ping eNodeB(s) and internet respectively.

    ```
    ping google.com -I eth0

    ping <enodeB IP> -I eth1
    ```
2. For managed eNB check status of eNodeB(s) attached to gateway using the cli(skip this step for unmanaged eNB):
    ```
    sudo enodebd_cli.py get_all_status
    ```

## Magma Services

1. Check all gateway services and their status by running below commands.

    ```
    sudo service magma@* status

    sudo service scptd status

    service openvswitch-switch status
    ```
    1. Confirm that all services are in an "active (running)" state without any errors.
    2. Monitor the duration services have been running to detect unexpected restarts.
    3. Example: If a service has been running for 3 minutes and 35 seconds, investigate further.
    4. Check that the memory usage of services does not exceed their assigned limit.
    5. Example: If a service uses 113.9MB out of an allocated 512MB, it should be within the memory limit.
2. Check the status of OVS module with sudo ovs-vsctl show. Make sure the “is_connected” states are “true” and there are any port errors.
    ```
    sudo ovs-vsctl show
    ```

## Orchestrator Interface

1. Verify connectivity with Orchestrator by running below command: 

    ```
    checkin_cli.py
    ```

2. Verify in syslogs AGW is perioridically checkin in to Orc8r. Around every minute you should see this message Checkin Successful! Successfully sent state. Syslogs can be found in **/var/log/syslog**

3. Verify if AGW was successfully checkin in NMS(Show as "Good" Health)


## Subscribers
Check subscribers attached using the below command:
```
sudo mobility_cli.py get_subscriber_table
```

## Performance
Check CPU utilization. **top.** If it is high, check which process is utilizing CPU more from output of the same command. All processes are listed there.

Check memory utilization by running the same command as above. You can also verify by service using the command
```
 ps -o pid,user,%mem,command ax | sort -b -k3 -r
```

## Metrics
Login to NMS UI. From the left side menu options, select “Metrics”. Check various metrics that are available. Look for any sudden spike or degradation that may indicate issues with the system.

- Number of Connected eNBs (Grafana -> Dashboards -> Networks)
- Network of Connected UE (Grafana -> Dashboards -> Networks)
- Network of Registered UE (Grafana -> Dashboards -> Networks)
- Attach/ Reg attempts (Grafana -> Dashboards -> Networks)
- Attach Success Rate (Grafana -> Dashboards -> Networks)
- S6a Authentication Success Rate (Grafana -> Dashboards -> Networks)
- Service Request Success Rate (Grafana -> Dashboards -> Networks)
- Session Create Success Rate (Grafana -> Dashboards -> Networks)
- Upload/Download Throughput (Grafana -> Dashboards -> Gateway)

Note: Number of sites(enodeb) down, users affected, and outage duration are key indicators of service impact.

## Optional Features
Make sure you test any other feature that is applicable to your network

- X2 Handover
- S1-Flex
- Inbound Roaming
- External DHCP
- UE Bridge Mode