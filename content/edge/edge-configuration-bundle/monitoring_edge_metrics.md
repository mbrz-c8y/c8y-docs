---
weight: 90
title: Monitoring the Edge metrics
layout: bundle
section:
  - edge_server
---

In your {{< product-c8y-iot >}} tenant, you can monitor the measurements of the Edge appliance listed in the table below:

|<div style="width:150px">Measurement</div>|<div style="width:250px">Metrics</div>|Description
|:---|:---|:---
|Disk space|- Total disk space<br>- Free disk space<br>- Used disk space<br>- Percentage of used disk space|The Edge appliance sends the disk space metrics as a measurement for both installation disk and data disk, every 10 minutes. The measurements are sent in gigabytes (GB) rounded to two decimal places. The percentage is rounded to one decimal place. The data points for this measurement are:<br><br> - *c8y_InstallationDisk*<br>- *c8y_DataDisk*<br><br>If {{< product-c8y-iot >}} Edge is unable to read the metrics from the installation disk or the data disk, an alarm is sent to the {{< product-c8y-iot >}} tenant. The alarms have a minor severity and the data points for the alarms are:<br><br>- *c8y_FileSystemMeasurementErrorInstallationDisk*<br>- *c8y_FileSystemMeasurementErrorDataDisk*
|Memory (RAM)|- Total RAM<br>- Free RAM<br>- Used RAM<br>- Percentage of RAM used|The Edge appliance sends the memory usage metrics as a measurement every 5 seconds in gibibytes (GiB). The data point for this measurement is *c8y_Memory*<br><br>If {{< product-c8y-iot >}} Edge is unable to read the metrics from the memory, an alarm is sent to the {{< product-c8y-iot >}} tenant. The data point for the alarm is:<br><br>- *c8y_MemoryMeasurementError*.
|CPU|Percentage of CPU used<br><br>Unit: Percentage|The Edge appliance sends the percentage of CPU used at intervals over 5 seconds, 60 seconds, and 600 seconds. The data points for this measurement are:<br><br>- *c8y_CpuUsage5Seconds*<br>- *c8y_CpuUsage60Seconds*<br>- *c8y_CpuUsage600Seconds*<br><br>If {{< product-c8y-iot >}} Edge is unable to read the metrics from the CPU, an alarm is sent to the {{< product-c8y-iot >}} tenant. The data point for the alarm is:<br><br>- *c8y_CPUMeasurementError*.
|Disk I/O|- Data read per second<br>- Data written per second<br><br>Unit: KB/s|The Edge appliance sends the disk input/output metrics as a measurement for both installation disk and data disk at intervals over 5 seconds, 60 seconds, and 600 seconds. The data points for this measurement are:<br><br>- *c8y_DataDiskIo5Seconds*<br>- *c8y_DataDiskIo60Seconds*<br>- *c8y_DataDiskIo600Seconds*<br>- *c8y_InstallationDiskIo5Seconds*<br>- *c8y_InstallationDiskIo60Seconds*<br>- *c8y_InstallationDiskIo5Seconds*<br><br>If {{< product-c8y-iot >}} Edge is unable to read the metrics from the disk, an alarm is sent to the {{< product-c8y-iot >}} tenant. The data point for the alarm is:<br><br>- *c8y_DiskIOMeasurementError*.
|Network|- Data and packets sent per second<br>- Data and packets received per second<br><br>Unit: KB/s and packets/s|The Edge appliance sends the network metrics as a measurement at intervals over 5 seconds, 60 seconds, and 600 seconds. The data points for this measurement are:<br><br>- *c8y_NetworkInterface_lo-5Seconds*<br>- *c8y_NetworkInterface_lo-60Seconds*<br>- *c8y_NetworkInterface_lo-600Seconds*<br><br>If {{< product-c8y-iot >}} Edge is unable to read the metrics from the network, an alarm is sent to the {{< product-c8y-iot >}} tenant. The data point for the alarm is:<br><br>- *c8y_NetworkIoMeasurementError*.

To monitor the metrics in your {{< product-c8y-iot >}} tenant, you can create a dashboard and add widgets in the Cockpit application of your tenant. For more information about creating dashboards, see [Cockpit > Dashboards](/users-guide/cockpit/#dashboards) in the *User guide*.

Also, you can define smart rules to create alerts or raise alarms for the metrics. For example, when the free disk space is less than 5 GB, create an alert. For more information about smart rules, see [Cockpit > Smart rules](/users-guide/cockpit/#smart-rules) in the *User guide*.  