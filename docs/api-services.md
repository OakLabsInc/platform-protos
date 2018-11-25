# Protocol Documentation
<a name="top"/>

## Table of Contents

- [application.proto](#application.proto)
    - [ApplicationDefinition](#oak.platform.ApplicationDefinition)
    - [ApplicationDefinition.DockerService](#oak.platform.ApplicationDefinition.DockerService)
    - [ApplicationSource](#oak.platform.ApplicationSource)
    - [ApplicationStatus](#oak.platform.ApplicationStatus)
    - [InstallStatus](#oak.platform.InstallStatus)
    - [LogBatch](#oak.platform.LogBatch)
    - [LogBatch.LogLine](#oak.platform.LogBatch.LogLine)
  
    - [InstallStatus.InstallStep](#oak.platform.InstallStatus.InstallStep)
  
  
    - [Application](#oak.platform.Application)
  

- [audio.proto](#audio.proto)
    - [AudioConfiguration](#oak.platform.AudioConfiguration)
    - [AudioConfigurationRequest](#oak.platform.AudioConfigurationRequest)
    - [AudioInformation](#oak.platform.AudioInformation)
    - [AudioInformation.Mixer](#oak.platform.AudioInformation.Mixer)
  
  
  
    - [Audio](#oak.platform.Audio)
  

- [automatic.proto](#automatic.proto)
    - [Configuration](#oak.platform.Configuration)
  
  
  
    - [Automatic](#oak.platform.Automatic)
  

- [display.proto](#display.proto)
    - [DisplayConfiguration](#oak.platform.DisplayConfiguration)
    - [DisplayConfigurationRequest](#oak.platform.DisplayConfigurationRequest)
    - [DisplayGlobalConfiguration](#oak.platform.DisplayGlobalConfiguration)
    - [DisplayInformation](#oak.platform.DisplayInformation)
    - [DisplayInformation.Display](#oak.platform.DisplayInformation.Display)
  
    - [DisplayConfiguration.Reflect](#oak.platform.DisplayConfiguration.Reflect)
    - [DisplayConfiguration.Rotate](#oak.platform.DisplayConfiguration.Rotate)
  
  
    - [Display](#oak.platform.Display)
  

- [host.proto](#host.proto)
    - [HostInformation](#oak.platform.HostInformation)
    - [ModuleList](#oak.platform.ModuleList)
    - [ModuleStatusList](#oak.platform.ModuleStatusList)
    - [ModuleStatusList.ModuleStatus](#oak.platform.ModuleStatusList.ModuleStatus)
  
  
  
    - [Host](#oak.platform.Host)
  

- [network.proto](#network.proto)
    - [NetworkInformation](#oak.platform.NetworkInformation)
    - [NetworkInformation.Device](#oak.platform.NetworkInformation.Device)
    - [NetworkManagerConfiguration](#oak.platform.NetworkManagerConfiguration)
    - [WiFiConnectionSettings](#oak.platform.WiFiConnectionSettings)
    - [WiFiNetworkList](#oak.platform.WiFiNetworkList)
    - [WiFiScanResults](#oak.platform.WiFiScanResults)
    - [WiFiScanResults.AccessPoint](#oak.platform.WiFiScanResults.AccessPoint)
  
    - [NetworkInformation.Technology](#oak.platform.NetworkInformation.Technology)
  
  
    - [Network](#oak.platform.Network)
  

- [touch.proto](#touch.proto)
    - [TouchConfiguration](#oak.platform.TouchConfiguration)
    - [TouchConfigurationRequest](#oak.platform.TouchConfigurationRequest)
    - [TouchInformation](#oak.platform.TouchInformation)
    - [TouchInformation.TouchDevice](#oak.platform.TouchInformation.TouchDevice)
  
    - [TouchConfiguration.Orientation](#oak.platform.TouchConfiguration.Orientation)
  
  
    - [Touch](#oak.platform.Touch)
  

- [Scalar Value Types](#scalar-value-types)



<a name="application.proto"/>
<p align="right"><a href="#top">Top</a></p>

## application.proto



<a name="oak.platform.ApplicationDefinition"/>

### ApplicationDefinition



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| services | [ApplicationDefinition.DockerService](#oak.platform.ApplicationDefinition.DockerService) | repeated |  |






<a name="oak.platform.ApplicationDefinition.DockerService"/>

### ApplicationDefinition.DockerService



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| image | [string](#string) |  | Identifies a Docker image. Format is &#34;[REGISTRY_HOST[:REGISTRY_PORT]/]NAME[:TAG]&#34; e.g. &#34;index.docker.io/oaklabs/oak:1.0.0&#34; If REGISTRY_HOST is not specified, &#39;index.docker.io&#39; (Docker Hub) is the default If TAG is not specified, &#39;:latest&#39; is the default |
| username | [string](#string) |  | Username to use when pulling this image For images served publicly this can be left blank |
| password | [string](#string) |  | Password for the specified username Passwords will NOT be stored by platform server at all; they are used at Install time and then forgotten |
| environment | [ApplicationDefinition.DockerService.EnvironmentEntry](#oak.platform.ApplicationDefinition.DockerService.EnvironmentEntry) | repeated | Environment variables to be set for just this Docker container The key and values in this mapping will be the name and value of the environment variables. The key must contain only upper-case letters, digits and &#39;_&#39; and not start with a digit &#39;value&#39; can be any single-line string, quotes are not necessary |
| assets | [ApplicationDefinition.DockerService.AssetsEntry](#oak.platform.ApplicationDefinition.DockerService.AssetsEntry) | repeated | Files to be mounted read-only in this Docker container This is intended for configuration and credential files The key must be an absolute path where the file should be mounted at and the value is the contents of the file. |






<a name="oak.platform.ApplicationSource"/>

### ApplicationSource



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| docker_compose_yaml | [string](#string) |  |  |






<a name="oak.platform.ApplicationStatus"/>

### ApplicationStatus



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| running | [bool](#bool) |  | Whether the application is currently running |
| failed | [bool](#bool) |  | If the application is stopped, whether it crashed or was deliberately stopped |
| since | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |  | Timestamp according to the unit&#39;s clock when the application status last changed |






<a name="oak.platform.InstallStatus"/>

### InstallStatus



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| step | [InstallStatus.InstallStep](#oak.platform.InstallStatus.InstallStep) |  |  |
| details | [string](#string) |  |  |






<a name="oak.platform.LogBatch"/>

### LogBatch



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| loglines | [LogBatch.LogLine](#oak.platform.LogBatch.LogLine) | repeated |  |






<a name="oak.platform.LogBatch.LogLine"/>

### LogBatch.LogLine



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| text | [string](#string) |  |  |
| timestamp | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |  |  |





 


<a name="oak.platform.InstallStatus.InstallStep"/>

### InstallStatus.InstallStep


| Name | Number | Description |
| ---- | ------ | ----------- |
| UNKNOWN_STEP | 0 | This should never be used |
| BEGIN | 1 | First message, streamed immediately |
| END | 2 | Final message, details will contain docker-compose.yaml |
| PULL_BEGIN | 3 | Indicates the next Docker images is about to be pulled, details contains image name |
| PULLING | 7 | Details about image currently being pulled, details will be JSON |
| PULL_END | 4 | Indicates Docker image pull is complete |
| WRITE_BEGIN | 5 | Indicates new docker-compose.yaml is about to be generated and written |
| WRITE_END | 6 | Indicates writing docker-compose.yaml was successful |


 

 


<a name="oak.platform.Application"/>

### Application
Manage the user&#39;s application. Application are defined by
docker-compose.yaml files.

The host will hold two application versions called LIVE and
IDLE. Both are docker-compose.yaml files.

The LIVE version is the version that is actually run.

The IDLE version is a placeholder where new applications can be
installed.

When a new version is installed as the IDLE version, it can then
be deployed by swapping the LIVE and IDLE versions. They can then
be swapped again to roll back if necessary.

To DEPLOY an application, you will need to use Install and
SwapIdleAndLive at least.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Status | [.google.protobuf.Empty](#google.protobuf.Empty) | [ApplicationStatus](#google.protobuf.Empty) | Shows whether application is running, whether it crashed if it is not running, and the time that it entered its current state. |
| Start | [.google.protobuf.Empty](#google.protobuf.Empty) | [.google.protobuf.Empty](#google.protobuf.Empty) | Starts the LIVE application (if it is not already started) |
| Stop | [.google.protobuf.Empty](#google.protobuf.Empty) | [.google.protobuf.Empty](#google.protobuf.Empty) | Stops the LIVE application (if it is not already stopped) |
| Install | [ApplicationDefinition](#oak.platform.ApplicationDefinition) | [InstallStatus](#oak.platform.ApplicationDefinition) | Generates a new IDLE version from a given set of Docker tags and credentials, then pulls the necessary Docker images. Status reports are streamed back for each pull. The final message will contain the new docker-compose.yaml just like ViewIdle response.

If any devices matching the globs below are present when an app is installed then they must be present when the app is started: /dev/video* /dev/ttyACM* /dev/nvidia0 /dev/nvidiactl |
| ViewIdle | [.google.protobuf.Empty](#google.protobuf.Empty) | [ApplicationSource](#google.protobuf.Empty) | Shows the IDLE version docker-compose.yaml. |
| ViewLive | [.google.protobuf.Empty](#google.protobuf.Empty) | [ApplicationSource](#google.protobuf.Empty) | Shows the LIVE version docker-compose.yaml. |
| SwapIdleAndLive | [.google.protobuf.Empty](#google.protobuf.Empty) | [.google.protobuf.Empty](#google.protobuf.Empty) | Stops the application (if not already stopped), switches the LIVE and IDLE versions, and then starts the application using the new LIVE version regardless of whether it was running before. This is the last step to DEPLOY an application. It is also used to ROLLBACK. |
| FactoryReset | [.google.protobuf.Empty](#google.protobuf.Empty) | [.google.protobuf.Empty](#google.protobuf.Empty) | Erases both the LIVE and IDLE versions and write the default application as both |
| Logs | [.google.protobuf.Empty](#google.protobuf.Empty) | [LogBatch](#google.protobuf.Empty) | Streams application logs. Multiple lines are batched every second to limit the number of messages streamed. |

 



<a name="audio.proto"/>
<p align="right"><a href="#top">Top</a></p>

## audio.proto



<a name="oak.platform.AudioConfiguration"/>

### AudioConfiguration



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| mute | [bool](#bool) |  |  |
| volume | [uint32](#uint32) |  | Must be between 0 and 100 inclusive 0 is effectively mute and 100 is maximum volume |






<a name="oak.platform.AudioConfigurationRequest"/>

### AudioConfigurationRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| mixer_id | [string](#string) |  |  |
| configuration | [AudioConfiguration](#oak.platform.AudioConfiguration) |  |  |






<a name="oak.platform.AudioInformation"/>

### AudioInformation



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| mixers | [AudioInformation.Mixer](#oak.platform.AudioInformation.Mixer) | repeated |  |






<a name="oak.platform.AudioInformation.Mixer"/>

### AudioInformation.Mixer



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| mixer_id | [string](#string) |  |  |
| configuration | [AudioConfiguration](#oak.platform.AudioConfiguration) |  |  |





 

 

 


<a name="oak.platform.Audio"/>

### Audio
Configure audio devices that are connected to the host

Currently, only audio output devices are supported.
Microphones are not supported.

&#39;mixer_id&#39; values come from the available ports on the host
device regardless of whether an audio device is connected.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [AudioInformation](#google.protobuf.Empty) | Lists available mixers which correspond to connected audio devices; also shows the current configuration, i.e. volume and mute settings You may have to guess-and-check to determine which mixer corresponds to the physical device you want to control. |
| Configure | [AudioConfigurationRequest](#oak.platform.AudioConfigurationRequest) | [.google.protobuf.Empty](#oak.platform.AudioConfigurationRequest) | Applies configuration to an audio device, i.e. change the volume |

 



<a name="automatic.proto"/>
<p align="right"><a href="#top">Top</a></p>

## automatic.proto



<a name="oak.platform.Configuration"/>

### Configuration
The Configuration message contains configuration request messages
from other services. See the matching .proto files.


| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| audio | [AudioConfigurationRequest](#oak.platform.AudioConfigurationRequest) | repeated |  |
| display | [DisplayConfigurationRequest](#oak.platform.DisplayConfigurationRequest) | repeated |  |
| display_global | [DisplayGlobalConfiguration](#oak.platform.DisplayGlobalConfiguration) |  |  |
| OBSOLETE_wifi | [WiFiConnectionSettings](#oak.platform.WiFiConnectionSettings) | repeated |  |
| touch | [TouchConfigurationRequest](#oak.platform.TouchConfigurationRequest) | repeated |  |





 

 

 


<a name="oak.platform.Automatic"/>

### Automatic
Enables configuration when the Platform starts.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Store | [Configuration](#oak.platform.Configuration) | [.google.protobuf.Empty](#oak.platform.Configuration) | Stores a Configuration for automatic application on start-up |
| View | [.google.protobuf.Empty](#google.protobuf.Empty) | [Configuration](#google.protobuf.Empty) | Exposes the currently stored Configuration |
| Clear | [.google.protobuf.Empty](#google.protobuf.Empty) | [.google.protobuf.Empty](#google.protobuf.Empty) | Erases the currently stored Configuration so that no automatic configuration will be done on next Platform start-up. |
| Generate | [.google.protobuf.Empty](#google.protobuf.Empty) | [Configuration](#google.protobuf.Empty) | Creates a Configuration message that, when sent to the Store RPC, would lead to automatic configuration resulting in the same settings that are in place when Generate was called |
| Apply | [.google.protobuf.Empty](#google.protobuf.Empty) | [.google.protobuf.Empty](#google.protobuf.Empty) | Uses the stored Configuration message to configure the appropriate other services |

 



<a name="display.proto"/>
<p align="right"><a href="#top">Top</a></p>

## display.proto



<a name="oak.platform.DisplayConfiguration"/>

### DisplayConfiguration



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| enabled | [bool](#bool) |  | setting &#39;false&#39; will turn the display off and other settings will have no effect |
| mode | [string](#string) |  | resolution and framerate; values should only come from Info endpoint and should not be guessed |
| reflect | [DisplayConfiguration.Reflect](#oak.platform.DisplayConfiguration.Reflect) |  | mirror the image across either axis or both |
| rotate | [DisplayConfiguration.Rotate](#oak.platform.DisplayConfiguration.Rotate) |  | rotate the image relative to the display&#39;s upright direction NOT relative to the image&#39;s current rotation |
| transform | [string](#string) |  | transformation matrix to apply to output see &#39;--transform&#39; instructions here: https://www.x.org/archive/current/doc/man/man1/xrandr.1.xhtml must be 9 comma-separated decimal values |






<a name="oak.platform.DisplayConfigurationRequest"/>

### DisplayConfigurationRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| display_id | [string](#string) |  |  |
| configuration | [DisplayConfiguration](#oak.platform.DisplayConfiguration) |  |  |






<a name="oak.platform.DisplayGlobalConfiguration"/>

### DisplayGlobalConfiguration



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| dpi | [uint32](#uint32) |  | set DPI for all displays |






<a name="oak.platform.DisplayInformation"/>

### DisplayInformation



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| global_configuration | [DisplayGlobalConfiguration](#oak.platform.DisplayGlobalConfiguration) |  |  |
| displays | [DisplayInformation.Display](#oak.platform.DisplayInformation.Display) | repeated |  |






<a name="oak.platform.DisplayInformation.Display"/>

### DisplayInformation.Display



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| display_id | [string](#string) |  |  |
| configuration | [DisplayConfiguration](#oak.platform.DisplayConfiguration) |  |  |
| preferred_mode | [string](#string) |  | the native resolution and framerate of the display |
| available_modes | [string](#string) | repeated |  |





 


<a name="oak.platform.DisplayConfiguration.Reflect"/>

### DisplayConfiguration.Reflect


| Name | Number | Description |
| ---- | ------ | ----------- |
| NO_REFLECT | 0 |  |
| X | 1 | swap top and bottom |
| Y | 2 | swap left and right |
| XY | 3 | swap along both axes |



<a name="oak.platform.DisplayConfiguration.Rotate"/>

### DisplayConfiguration.Rotate


| Name | Number | Description |
| ---- | ------ | ----------- |
| NO_ROTATE | 0 |  |
| LEFT | 1 | turn 90 degrees counter-clockwise |
| RIGHT | 2 | turn 90 degrees clockwise |
| INVERTED | 3 | turn 180 degrees |


 

 


<a name="oak.platform.Display"/>

### Display
Configure displays (monitors, TVs, etc) that are connected to the host

A &#34;mode&#34; is a string representing a resolution and framerate
together, e.g. &#34;1024x768@60.00&#34;. Because values for modes must be
an exact text match in order to be recognized they should only be
generated by this service. Users should not attempt to apply a
mode to a display if it is not listed in that display&#39;s
&#39;available_modes&#39;.

When in doubt, it is recommended that every display is configured
with its preferred_mode and the DPI be set to 96.

&#39;display_id&#39; values come from the name of the physical port the
display is plugged into.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [DisplayInformation](#google.protobuf.Empty) | Lists displays, current configuration and supported configurations |
| Configure | [DisplayConfigurationRequest](#oak.platform.DisplayConfigurationRequest) | [.google.protobuf.Empty](#oak.platform.DisplayConfigurationRequest) | Applies configuration to a specific display |
| ConfigureGlobal | [DisplayGlobalConfiguration](#oak.platform.DisplayGlobalConfiguration) | [.google.protobuf.Empty](#oak.platform.DisplayGlobalConfiguration) | Applies configuration that affects all displays |

 



<a name="host.proto"/>
<p align="right"><a href="#top">Top</a></p>

## host.proto



<a name="oak.platform.HostInformation"/>

### HostInformation



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| hostname | [string](#string) |  | Globally unique identifier for the host |
| time | [google.protobuf.Timestamp](#google.protobuf.Timestamp) |  | Current time according to host&#39;s clock |
| timezone | [string](#string) |  | Timezone host is configured to use e.g. &#34;America/Los_Angeles&#34; |
| oakos_version | [string](#string) |  |  |
| platform_version | [string](#string) |  |  |






<a name="oak.platform.ModuleList"/>

### ModuleList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| module_ids | [string](#string) | repeated |  |






<a name="oak.platform.ModuleStatusList"/>

### ModuleStatusList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| modules | [ModuleStatusList.ModuleStatus](#oak.platform.ModuleStatusList.ModuleStatus) | repeated |  |






<a name="oak.platform.ModuleStatusList.ModuleStatus"/>

### ModuleStatusList.ModuleStatus



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| module_id | [string](#string) |  |  |
| active | [bool](#bool) |  |  |





 

 

 


<a name="oak.platform.Host"/>

### Host
Expose information and control specific to the host and not related
to any specific hardware

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [HostInformation](#google.protobuf.Empty) | Exposes hostname, current time and timezone of host |
| Reboot | [.google.protobuf.Empty](#google.protobuf.Empty) | [.google.protobuf.Empty](#google.protobuf.Empty) | Reboots the host immediately |

 



<a name="network.proto"/>
<p align="right"><a href="#top">Top</a></p>

## network.proto



<a name="oak.platform.NetworkInformation"/>

### NetworkInformation



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| devices | [NetworkInformation.Device](#oak.platform.NetworkInformation.Device) | repeated |  |






<a name="oak.platform.NetworkInformation.Device"/>

### NetworkInformation.Device



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| device_id | [string](#string) |  |  |
| technology | [NetworkInformation.Technology](#oak.platform.NetworkInformation.Technology) |  |  |
| hardware_address | [string](#string) |  | aka &#34;MAC Address&#34; |
| ssid | [string](#string) |  | string state = 4; string connection_id = 5; |
| addresses | [string](#string) | repeated |  |
| gateway | [string](#string) |  |  |






<a name="oak.platform.NetworkManagerConfiguration"/>

### NetworkManagerConfiguration



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| connection_file | [string](#string) | repeated | Typically, there would be one file for each network the unit needs to be able to join. These files are normally generated via nm-connection-editor. The recommended work-flow is to set up and test a connection locally and then copy the generated file removing any unnecessary or conflicting fields such as those that contain hardware addresses. Note that &#39;[main]/uuid&#39; is required. |
| asset_file | [string](#string) | repeated | Certificate files and other assets that a connection_file might reference. If a connection profile needs to reference a certificate, the certificate file can be provided in the &#39;asset_file&#39; array and then it will be placed at &#39;/network-asset/$N&#39; where $N is the 0-based index in &#39;asset_file&#39;. For example, if two asset files are provided then in a connection_file they can be referenced as &#39;/network-asset/0&#39; and &#39;/network-asset/1&#39;. |






<a name="oak.platform.WiFiConnectionSettings"/>

### WiFiConnectionSettings



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ssid | [string](#string) |  | Settings are WPA-PSK, also known as WPA-Personal. This is currently all that is supported. |
| passphrase | [string](#string) |  | &#39;passphrase&#39; will be stored securely and CANNOT be viewed. |






<a name="oak.platform.WiFiNetworkList"/>

### WiFiNetworkList



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| wifi_networks | [WiFiConnectionSettings](#oak.platform.WiFiConnectionSettings) | repeated |  |






<a name="oak.platform.WiFiScanResults"/>

### WiFiScanResults



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| visible_access_points | [WiFiScanResults.AccessPoint](#oak.platform.WiFiScanResults.AccessPoint) | repeated |  |






<a name="oak.platform.WiFiScanResults.AccessPoint"/>

### WiFiScanResults.AccessPoint



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| ssid | [string](#string) |  |  |
| hardware_address | [string](#string) |  |  |
| strength_percent | [uint32](#uint32) |  |  |





 


<a name="oak.platform.NetworkInformation.Technology"/>

### NetworkInformation.Technology


| Name | Number | Description |
| ---- | ------ | ----------- |
| UNKNOWN | 0 |  |
| ETHERNET | 1 | IEEE 802.3 |
| WIFI | 2 | IEEE 802.11 |


 

 


<a name="oak.platform.Network"/>

### Network
View and configure host&#39;s networking settings.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [NetworkInformation](#google.protobuf.Empty) | Shows network information for all Ethernet and WiFi devices, including current network addresses and MAC addresses. |
| WiFiScan | [.google.protobuf.Empty](#google.protobuf.Empty) | [WiFiScanResults](#google.protobuf.Empty) | Lists visible WiFi networks using the first available WiFi interface |
| AddWiFi | [WiFiConnectionSettings](#oak.platform.WiFiConnectionSettings) | [.google.protobuf.Empty](#oak.platform.WiFiConnectionSettings) | Adds or overwrites configuration for connecting to a specific WiFi network. The host will then attempt to connect to the network whenever it is available. These settings are persisted until `ForgetWifi` is used. |
| ForgetWiFi | [WiFiConnectionSettings](#oak.platform.WiFiConnectionSettings) | [.google.protobuf.Empty](#oak.platform.WiFiConnectionSettings) | Removes stored WiFi configuration. |
| ListKnownWiFiNetworks | [.google.protobuf.Empty](#google.protobuf.Empty) | [WiFiNetworkList](#google.protobuf.Empty) | Lists the WiFi network configurations that are available to this host. |
| FullyConfigureNetworkManager | [NetworkManagerConfiguration](#oak.platform.NetworkManagerConfiguration) | [.google.protobuf.Empty](#oak.platform.NetworkManagerConfiguration) | Erases any previously configured network settings and drops in provided NetworkManager connections. This supports all types of connection configuration that NetworkManager supports. The automatic connection for Ethernet ports will still be present unless overridden in a provided connection file. Because the configurations may contain passwords they CANNOT be viewed later. CAUTION! If wired connections are configured through this RPC then the automatic DHCP connection may be lost. If all connections become invalid or unusable, the only route of recovery may be to re-install the OS. |

 



<a name="touch.proto"/>
<p align="right"><a href="#top">Top</a></p>

## touch.proto



<a name="oak.platform.TouchConfiguration"/>

### TouchConfiguration



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| calibration | [string](#string) |  | Four space-separated integers representing &lt;min-x max-x min-y max-y&gt; Use empty-string to use default calibration. Note that once calibration is changed it can only be reset to default by rebooting. It is recommended that you start with extreme values, such as &#34;0 32768 0 32768&#34;, and then manually change values one axis at a time until physical touches are aligned as desired. |
| orientation | [TouchConfiguration.Orientation](#oak.platform.TouchConfiguration.Orientation) |  | Direction the plane of touch is oriented relative to the touch interface&#39;s upright orientation. This is configured independently of any display&#39;s orientation. FORWARD_* means facing the user as a monitor normally does BACKWARD_* means turned around (the X axis is reversed) before rotating LEFT and RIGHT mean quarter turns relative to user&#39;s perspective |






<a name="oak.platform.TouchConfigurationRequest"/>

### TouchConfigurationRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| touch_device_id | [string](#string) |  |  |
| configuration | [TouchConfiguration](#oak.platform.TouchConfiguration) |  |  |






<a name="oak.platform.TouchInformation"/>

### TouchInformation



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| touch_devices | [TouchInformation.TouchDevice](#oak.platform.TouchInformation.TouchDevice) | repeated |  |






<a name="oak.platform.TouchInformation.TouchDevice"/>

### TouchInformation.TouchDevice



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| touch_device_id | [string](#string) |  |  |
| configuration | [TouchConfiguration](#oak.platform.TouchConfiguration) |  |  |





 


<a name="oak.platform.TouchConfiguration.Orientation"/>

### TouchConfiguration.Orientation


| Name | Number | Description |
| ---- | ------ | ----------- |
| FORWARD_UPRIGHT | 0 |  |
| FORWARD_LEFT | 1 |  |
| FORWARD_RIGHT | 2 |  |
| FORWARD_INVERTED | 3 |  |
| BACKWARD_UPRIGHT | 4 |  |
| BACKWARD_LEFT | 5 |  |
| BACKWARD_RIGHT | 6 |  |
| BACKWARD_INVERTED | 7 |  |


 

 


<a name="oak.platform.Touch"/>

### Touch
Configure human touch interfaces including IR and capacitive sensors

&#39;touch_device_id&#39; values come from serial numbers reported by the
touch devices themselves.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [TouchInformation](#google.protobuf.Empty) | Lists touch interfaces that can be configured |
| Configure | [TouchConfigurationRequest](#oak.platform.TouchConfigurationRequest) | [TouchConfiguration](#oak.platform.TouchConfigurationRequest) | Applies configuration to a touch interface |

 



## Scalar Value Types

| .proto Type | Notes | C++ Type | Java Type | Python Type |
| ----------- | ----- | -------- | --------- | ----------- |
| <a name="double" /> double |  | double | double | float |
| <a name="float" /> float |  | float | float | float |
| <a name="int32" /> int32 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint32 instead. | int32 | int | int |
| <a name="int64" /> int64 | Uses variable-length encoding. Inefficient for encoding negative numbers – if your field is likely to have negative values, use sint64 instead. | int64 | long | int/long |
| <a name="uint32" /> uint32 | Uses variable-length encoding. | uint32 | int | int/long |
| <a name="uint64" /> uint64 | Uses variable-length encoding. | uint64 | long | int/long |
| <a name="sint32" /> sint32 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int32s. | int32 | int | int |
| <a name="sint64" /> sint64 | Uses variable-length encoding. Signed int value. These more efficiently encode negative numbers than regular int64s. | int64 | long | int/long |
| <a name="fixed32" /> fixed32 | Always four bytes. More efficient than uint32 if values are often greater than 2^28. | uint32 | int | int |
| <a name="fixed64" /> fixed64 | Always eight bytes. More efficient than uint64 if values are often greater than 2^56. | uint64 | long | int/long |
| <a name="sfixed32" /> sfixed32 | Always four bytes. | int32 | int | int |
| <a name="sfixed64" /> sfixed64 | Always eight bytes. | int64 | long | int/long |
| <a name="bool" /> bool |  | bool | boolean | boolean |
| <a name="string" /> string | A string must always contain UTF-8 encoded or 7-bit ASCII text. | string | String | str/unicode |
| <a name="bytes" /> bytes | May contain any arbitrary sequence of bytes. | string | ByteString | str |

