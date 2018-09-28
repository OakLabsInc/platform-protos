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
  

- [oak-lights.proto](#oak-lights.proto)
    - [ChangeColorRequest](#oak.platform.ChangeColorRequest)
    - [ChangeColorRequest.Color](#oak.platform.ChangeColorRequest.Color)
    - [ControllerID](#oak.platform.ControllerID)
    - [OakLightsInformation](#oak.platform.OakLightsInformation)
    - [OakLightsInformation.OakLights](#oak.platform.OakLightsInformation.OakLights)
  
  
  
    - [OakLights](#oak.platform.OakLights)
  

- [oak-rfid.proto](#oak-rfid.proto)
    - [OakRFIDConfiguration](#oak.platform.OakRFIDConfiguration)
    - [OakRFIDConfigurationRequest](#oak.platform.OakRFIDConfigurationRequest)
    - [OakRFIDEvent](#oak.platform.OakRFIDEvent)
    - [OakRFIDFlashBoardRequest](#oak.platform.OakRFIDFlashBoardRequest)
    - [OakRFIDInformation](#oak.platform.OakRFIDInformation)
    - [OakRFIDInformation.OakRFIDDevice](#oak.platform.OakRFIDInformation.OakRFIDDevice)
    - [OakRFIDStreamRequest](#oak.platform.OakRFIDStreamRequest)
  
    - [OakRFIDConfiguration.Parser](#oak.platform.OakRFIDConfiguration.Parser)
    - [OakRFIDConfiguration.SearchMode](#oak.platform.OakRFIDConfiguration.SearchMode)
    - [OakRFIDEvent.Event](#oak.platform.OakRFIDEvent.Event)
  
  
    - [OakRFID](#oak.platform.OakRFID)
  

- [payment.proto](#payment.proto)
    - [PaymentConfiguration](#oak.platform.PaymentConfiguration)
    - [PaymentProvider](#oak.platform.PaymentProvider)
    - [PaymentServiceInfo](#oak.platform.PaymentServiceInfo)
    - [SaleRequest](#oak.platform.SaleRequest)
    - [SaleResponse](#oak.platform.SaleResponse)
    - [StandardSaleRequest](#oak.platform.StandardSaleRequest)
    - [StandardSaleResponse](#oak.platform.StandardSaleResponse)
  
    - [Currency](#oak.platform.Currency)
    - [PaymentProvider.BatchInterval](#oak.platform.PaymentProvider.BatchInterval)
    - [PaymentProviderType](#oak.platform.PaymentProviderType)
    - [PaymentSolutionType](#oak.platform.PaymentSolutionType)
    - [StandardSaleResponse.ResponseStatus](#oak.platform.StandardSaleResponse.ResponseStatus)
  
  
    - [Payment](#oak.platform.Payment)
  

- [touch.proto](#touch.proto)
    - [TouchConfiguration](#oak.platform.TouchConfiguration)
    - [TouchConfigurationRequest](#oak.platform.TouchConfigurationRequest)
    - [TouchInformation](#oak.platform.TouchInformation)
    - [TouchInformation.TouchDevice](#oak.platform.TouchInformation.TouchDevice)
  
  
  
    - [Touch](#oak.platform.Touch)
  

- [webcam.proto](#webcam.proto)
    - [JpgStream](#oak.platform.JpgStream)
    - [StreamRequest](#oak.platform.StreamRequest)
    - [WebcamInformation](#oak.platform.WebcamInformation)
    - [WebcamInformation.Webcam](#oak.platform.WebcamInformation.Webcam)
  
  
  
    - [Webcam](#oak.platform.Webcam)
  

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
| username | [string](#string) |  | Credentials to use when pulling this image passwords will NOT be stored by platform server at all For images served publicly these can be left blank |
| password | [string](#string) |  |  |






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
| Install | [ApplicationDefinition](#oak.platform.ApplicationDefinition) | [InstallStatus](#oak.platform.ApplicationDefinition) | Generates a new IDLE version from a given set of Docker tags and credentials, then pulls the necessary Docker images. Status reports are streamed back for each pull. The final message will contain the new docker-compose.yaml just like ViewIdle response. |
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
Exposes information and control specific to the host and not
related to any specific hardware.

Also enables control of Platform Modules, which can add more
functionality to the platform when desired. Modules are not enabled
by default to preserve system resources.

If an attempt is made to use an rpc provided by a module that is not
active it may return an 502 error.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [HostInformation](#google.protobuf.Empty) | Exposes hostname, current time and timezone of host |
| ListModules | [.google.protobuf.Empty](#google.protobuf.Empty) | [ModuleStatusList](#google.protobuf.Empty) | Lists the available Platform Modules and whether each is currently active and providing functionality |
| SetActiveModules | [ModuleList](#oak.platform.ModuleList) | [.google.protobuf.Empty](#oak.platform.ModuleList) | Enables the provided list of Platform Modules and disables those not listed. Use ListModules to see module_id values. |
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

 



<a name="oak-lights.proto"/>
<p align="right"><a href="#top">Top</a></p>

## oak-lights.proto



<a name="oak.platform.ChangeColorRequest"/>

### ChangeColorRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| controller_id | [string](#string) |  |  |
| rgb | [ChangeColorRequest.Color](#oak.platform.ChangeColorRequest.Color) |  |  |
| hex | [string](#string) |  | 3 or 6 digits with leading &#39;#&#39;, e.g. &#34;#F00&#34;, &#39;#A05020&#34; &#34;#FFFF00&#34; is invalid because 0 is not acceptable. |
| white | [uint32](#uint32) |  | The brightness of the white lights at end of transition. Must be between 1 and 255 inclusive. |
| duration | [uint32](#uint32) |  | The time in milliseconds for the transition to take. Must be positive. For fastest transition possible, use 1. |






<a name="oak.platform.ChangeColorRequest.Color"/>

### ChangeColorRequest.Color



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| r | [uint32](#uint32) |  | Each value must be between 1 and 255 inclusive. |
| g | [uint32](#uint32) |  |  |
| b | [uint32](#uint32) |  |  |






<a name="oak.platform.ControllerID"/>

### ControllerID



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| controller_id | [string](#string) |  |  |






<a name="oak.platform.OakLightsInformation"/>

### OakLightsInformation



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| controllers | [OakLightsInformation.OakLights](#oak.platform.OakLightsInformation.OakLights) | repeated |  |






<a name="oak.platform.OakLightsInformation.OakLights"/>

### OakLightsInformation.OakLights



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| controller_id | [string](#string) |  |  |





 

 

 


<a name="oak.platform.OakLights"/>

### OakLights
Control an Oak USB Lighting Controller.

The &#39;oak-lights&#39; module must be activated before these RPCs are
available.

&#39;controller_id&#39; values come from serial numbers reported by the
light controllers themselves.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [OakLightsInformation](#google.protobuf.Empty) | Lists controllers that are connected to the host |
| ChangeColor | [ChangeColorRequest](#oak.platform.ChangeColorRequest) | [.google.protobuf.Empty](#oak.platform.ChangeColorRequest) | Transitions the light color over a given amount of time |
| FlashBoard | [ControllerID](#oak.platform.ControllerID) | [.google.protobuf.Empty](#oak.platform.ControllerID) | Installs firmware on the controller |

 



<a name="oak-rfid.proto"/>
<p align="right"><a href="#top">Top</a></p>

## oak-rfid.proto



<a name="oak.platform.OakRFIDConfiguration"/>

### OakRFIDConfiguration



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| parser | [OakRFIDConfiguration.Parser](#oak.platform.OakRFIDConfiguration.Parser) |  | Determines how to parse the EPC |
| search_mode | [OakRFIDConfiguration.SearchMode](#oak.platform.OakRFIDConfiguration.SearchMode) |  |  |
| strength | [uint32](#uint32) |  | How strong a signal to use when scanning for RFID tags. Must be a multiple of 25 between 1000 and 3225 inclusive. |
| start_scan_interval | [uint32](#uint32) |  | The reader scans for tags in an interval. The interval starts at &#39;start_scan_interval&#39; and is doubled after every scan until it passes &#39;max_scan_interval&#39; and then that is used as the interval.

Tags are considered to have ENTERed view after they are detected by every scan within a period lasting for the asdf &#39;enter_threshold&#39;. Once they are considered in view, they EXIT view after they are NOT detected by every scan within a period lasting for the &#39;exit_threshold&#39;.

All of these times are specified in milliseconds. |
| max_scan_interval | [uint32](#uint32) |  |  |
| enter_threshold | [uint32](#uint32) |  |  |
| exit_threshold | [uint32](#uint32) |  |  |






<a name="oak.platform.OakRFIDConfigurationRequest"/>

### OakRFIDConfigurationRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| rfid_device_id | [string](#string) |  |  |
| configuration | [OakRFIDConfiguration](#oak.platform.OakRFIDConfiguration) |  |  |






<a name="oak.platform.OakRFIDEvent"/>

### OakRFIDEvent



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| event | [OakRFIDEvent.Event](#oak.platform.OakRFIDEvent.Event) |  |  |
| epc | [string](#string) |  | raw value from the RFID tag |
| upc | [string](#string) |  | UPC value translated from RFID tag |
| rssi | [sint32](#sint32) |  | Relative strength of the last tag read. Will be non-positive. See https://en.wikipedia.org/wiki/Received_signal_strength_indication |






<a name="oak.platform.OakRFIDFlashBoardRequest"/>

### OakRFIDFlashBoardRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| rfid_device_id | [string](#string) |  |  |






<a name="oak.platform.OakRFIDInformation"/>

### OakRFIDInformation



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| rfid_devices | [OakRFIDInformation.OakRFIDDevice](#oak.platform.OakRFIDInformation.OakRFIDDevice) | repeated |  |






<a name="oak.platform.OakRFIDInformation.OakRFIDDevice"/>

### OakRFIDInformation.OakRFIDDevice



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| rfid_device_id | [string](#string) |  |  |
| configuration | [OakRFIDConfiguration](#oak.platform.OakRFIDConfiguration) |  |  |






<a name="oak.platform.OakRFIDStreamRequest"/>

### OakRFIDStreamRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| rfid_device_id | [string](#string) |  |  |





 


<a name="oak.platform.OakRFIDConfiguration.Parser"/>

### OakRFIDConfiguration.Parser


| Name | Number | Description |
| ---- | ------ | ----------- |
| RAW | 0 | Do not parse EPC, pass through unaltered |
| UPC | 1 | Parse the EPC as a UPC |
| UPC14 | 2 | For cases where EPCs are encoded as UPCs with 14 digits |



<a name="oak.platform.OakRFIDConfiguration.SearchMode"/>

### OakRFIDConfiguration.SearchMode


| Name | Number | Description |
| ---- | ------ | ----------- |
| READER_SELECTED | 0 | When in doubt, use READER_SELECTED |
| DUAL_TARGET | 1 |  |
| SINGLE_TARGET | 2 |  |
| SINGLE_TARGET_WITH_SUPPRESSION | 3 |  |



<a name="oak.platform.OakRFIDEvent.Event"/>

### OakRFIDEvent.Event


| Name | Number | Description |
| ---- | ------ | ----------- |
| ENTER | 0 | indicates an RFID tag is in view |
| EXIT | 1 | indicates an RFID tag is no longer in view |


 

 


<a name="oak.platform.OakRFID"/>

### OakRFID
Control an Oak USB RFID Reader.

The &#39;oak-rfid&#39; module must be activated before these RPCs are
available.

&#39;rfid_device_id&#39; values come from serial numbers reported by the
RFID readers themselves.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [OakRFIDInformation](#google.protobuf.Empty) | Lists controllers that are connected to the host. |
| Configure | [OakRFIDConfigurationRequest](#oak.platform.OakRFIDConfigurationRequest) | [.google.protobuf.Empty](#oak.platform.OakRFIDConfigurationRequest) | Configures a controller before streaming begins. |
| Stream | [OakRFIDStreamRequest](#oak.platform.OakRFIDStreamRequest) | [OakRFIDEvent](#oak.platform.OakRFIDStreamRequest) | Streams events when RFID tags enter and exit range of the reader |
| FlashBoard | [OakRFIDFlashBoardRequest](#oak.platform.OakRFIDFlashBoardRequest) | [.google.protobuf.Empty](#oak.platform.OakRFIDFlashBoardRequest) | Installs firmware on the controller |

 



<a name="payment.proto"/>
<p align="right"><a href="#top">Top</a></p>

## payment.proto



<a name="oak.platform.PaymentConfiguration"/>

### PaymentConfiguration



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| providers | [PaymentProvider](#oak.platform.PaymentProvider) | repeated |  |






<a name="oak.platform.PaymentProvider"/>

### PaymentProvider



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| provider_name | [string](#string) |  | During configuration the provider name can be set to any value. Afterwards it will be referred to by this name when issuing a transaction. This allows multiple payment providers to be saved and selected between. |
| provider_type | [PaymentProviderType](#oak.platform.PaymentProviderType) |  | This selects the payment company that will facilitate transactions. |
| solution | [PaymentSolutionType](#oak.platform.PaymentSolutionType) |  | This selects the specific software product that will facilitate transactions. |
| host | [string](#string) |  | (Optional) This configures the API host that we will communicate with for this provider. It may be a local network address (for POS solutions) or a WAN address (for cloud). |
| api_id | [string](#string) |  | (Optional) Some solutions, particularly cloud, will require an api_id. Check the documentation for your specific provider/solution. |
| api_key | [string](#string) |  | (Optional) Some solutions, particularly cloud, will require an api_key. Check the documentation for your specific provider/solution. |
| batch_interval | [PaymentProvider.BatchInterval](#oak.platform.PaymentProvider.BatchInterval) |  | (Optional) This sets the batch interval for POS solutions. This is offered for convenience so that the application builder does not have to implement scheduling. If not set it defaults to &#39;OFF&#39;. |
| batch_hour | [int32](#int32) |  | (Optional) This sets the hour of day that batch processing will run. It defaults to midnight.

0-23 |






<a name="oak.platform.PaymentServiceInfo"/>

### PaymentServiceInfo



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| configured | [bool](#bool) |  | Status to represent whether the Configure service has been called. Financial transactions will fail unless this value is &#39;true&#39;. |
| configuration | [PaymentConfiguration](#oak.platform.PaymentConfiguration) |  | Current value of the configuration. |






<a name="oak.platform.SaleRequest"/>

### SaleRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| sale_request | [StandardSaleRequest](#oak.platform.StandardSaleRequest) |  | This section of the request contains generic properties used by all payment providers. This accounts for the most common payment use cases. To enable or configure functionality for your specific provider, see the request section that corresponds with your provider. |
| freedompay_request | [FreedomPayRequest](#oak.platform.FreedomPayRequest) |  | Options pertaining to FreedomPay. |






<a name="oak.platform.SaleResponse"/>

### SaleResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| provider_type | [PaymentProviderType](#oak.platform.PaymentProviderType) |  | The provider type that was selected for this sale. E.g. TEST, FREEDOMPAY, WORLDPAY, etc. |
| response | [StandardSaleResponse](#oak.platform.StandardSaleResponse) |  | Standardized fields that will be (mostly) present in every response, regardless of payment provider. Much of the information here will also be in the provider specific response. However, your application may have an easier time switching providers at a later time if you rely on these normalized fields when possible. This is provided purely for your convenience. |
| freedompay_response | [FreedomPayResponse](#oak.platform.FreedomPayResponse) |  | Fields specific to FreedomPay. Will be `null` if FREEDOMPAY is not the `provider_type`. |






<a name="oak.platform.StandardSaleRequest"/>

### StandardSaleRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| provider_name | [string](#string) |  | Name of one of the PaymentProviders provided in configuration. |
| amount | [int32](#int32) |  | Amount in cents. |
| currency | [Currency](#oak.platform.Currency) |  | Currency. Default USD. |
| transaction_id | [string](#string) |  | (Deprecated) Transaction ID will be generated by the payment provider. This field will be ignored. |
| store_id | [string](#string) |  | (Optional) Merchant may wish to associate the transaction with a store or location ID. |
| terminal_id | [int32](#int32) |  | (Optional) Merchant may wish to associate the transaction with a unique ID for the kiosk, checkout counter, or other device that the customer or sales clerk may interact with. |
| merchant_ref | [string](#string) |  | (Optional) Another field that the merchant may use to store a related ID. |
| invoice_number | [string](#string) |  | (Optional) Number for invoice or purchase order. |






<a name="oak.platform.StandardSaleResponse"/>

### StandardSaleResponse



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| status | [StandardSaleResponse.ResponseStatus](#oak.platform.StandardSaleResponse.ResponseStatus) |  | This is the main place to check if you want to know a high level status code on whether the request succeeded or the general category of error if one occurred. To know the specific error, check the error string, or the error fields specific to your selected provider. |
| error | [string](#string) |  | This may contain an error message given by the provider. It will be unmodified if possible. |
| sale_amount | [int32](#int32) |  | The sale amount you are requesting to charge the customer. |
| currency | [Currency](#oak.platform.Currency) |  | Currency to be charged in. Default USD. |
| masked_card_number | [string](#string) |  | May be the last 4 digits, or other format depending on the payment provider. No card numbers or personal information are retained by the Oak Payment service. A POS based solution may store personal information locally, particularly in the case of batched transactions. Please consult your provider specific documentation for more details. |
| name_on_card | [string](#string) |  | Cardholder name. May be included by payment provider. |
| transaction_id | [string](#string) |  | A unique transaction ID generated by the payment provider. |





 


<a name="oak.platform.Currency"/>

### Currency


| Name | Number | Description |
| ---- | ------ | ----------- |
| USD | 0 | default currency is USD |



<a name="oak.platform.PaymentProvider.BatchInterval"/>

### PaymentProvider.BatchInterval


| Name | Number | Description |
| ---- | ------ | ----------- |
| OFF | 0 | Don&#39;t run batch transactions automatically. The application can still trigger them manually however. |
| DAILY | 1 | Run batch transactions daily. |
| WEEKLY | 2 | Run batch transactions weekly. |



<a name="oak.platform.PaymentProviderType"/>

### PaymentProviderType


| Name | Number | Description |
| ---- | ------ | ----------- |
| TEST | 0 | Test provider. Sends an arbitrary success response unless otherwise configured. Does not talk to any payment provider or activate the physical card reader. |
| FREEDOMPAY | 1 | FreedomPay provider. Can be configured for development and production. |



<a name="oak.platform.PaymentSolutionType"/>

### PaymentSolutionType


| Name | Number | Description |
| ---- | ------ | ----------- |
| DEFAULT | 0 | Default should be the POS solution if it is available. Some providers may not support POS however. Check provider specific documentation to determine the default. |
| POS | 1 | POS solution uses a local POS service, usually with a builtin queue and offline batch capabilities. These solutions are often prefered for kiosk implementations as they can continue to process transactions during network outages. |
| CLOUD | 2 | Cloud solution uses a provider-hosted solution. This means less moving parts locally, but cannot process transactions during a network outage. |



<a name="oak.platform.StandardSaleResponse.ResponseStatus"/>

### StandardSaleResponse.ResponseStatus


| Name | Number | Description |
| ---- | ------ | ----------- |
| INTERNAL_ERROR | 0 | something internal failed |
| ACCEPTED | 1 | success |
| REJECTED | 2 | insufficient funds, bad card, etc. |
| INPUT_ERROR | 3 | bad input |


 

 


<a name="oak.platform.Payment"/>

### Payment
Unified payment service which supports multiple payment providers.
Current providers include:
- TEST
- FREEDOMPAY

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [PaymentServiceInfo](#google.protobuf.Empty) | Shows whether application is running, whether it crashed if it is not running, and the time that it entered its current state. |
| Configure | [PaymentConfiguration](#oak.platform.PaymentConfiguration) | [.google.protobuf.Empty](#oak.platform.PaymentConfiguration) | This must be run after the service starts and before running any transactions. The purpose of this service is to choose a payment provider and associated options. |
| Sale | [SaleRequest](#oak.platform.SaleRequest) | [SaleResponse](#oak.platform.SaleRequest) | The Sale service performs an Authorization and Capture. This makes it a convenient single transaction which will perform a sale. |

 



<a name="touch.proto"/>
<p align="right"><a href="#top">Top</a></p>

## touch.proto



<a name="oak.platform.TouchConfiguration"/>

### TouchConfiguration



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| calibration | [string](#string) |  | Four space-separated integers representing &lt;min-x max-x min-y max-y&gt; It is recommended that you start with extreme values, such as &#34;0 32768 0 32768&#34;, and then manually change values one axis at a time until physical touches are aligned as desired |
| swap_axes | [bool](#bool) |  | Whether to swap the X and Y axis should be True if your touch interface is rotated LEFT or RIGHT relative to the display is overlays should be False if it is upright or inverted relative to the display it overlays |






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





 

 

 


<a name="oak.platform.Touch"/>

### Touch
Configure human touch interfaces including IR and capacitive sensors

&#39;touch_device_id&#39; values come from serial numbers reported by the
touch devices themselves.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [TouchInformation](#google.protobuf.Empty) | Lists touch interfaces that can be configured |
| Configure | [TouchConfigurationRequest](#oak.platform.TouchConfigurationRequest) | [TouchConfiguration](#oak.platform.TouchConfigurationRequest) | Applies configuration to a touch interface |

 



<a name="webcam.proto"/>
<p align="right"><a href="#top">Top</a></p>

## webcam.proto



<a name="oak.platform.JpgStream"/>

### JpgStream



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| url | [string](#string) |  | The local URL where a stream can be reached. |






<a name="oak.platform.StreamRequest"/>

### StreamRequest



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| webcam_id | [string](#string) |  |  |
| mode | [string](#string) |  | Specifies the resolution and framerate the camera should use for this stream. Must be a value from the &#39;available_modes&#39; list for the specified webcam. |
| port | [string](#string) |  | The port the stream should be served on. It is up to the caller to decide which available port to use. |






<a name="oak.platform.WebcamInformation"/>

### WebcamInformation



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| webcams | [WebcamInformation.Webcam](#oak.platform.WebcamInformation.Webcam) | repeated |  |






<a name="oak.platform.WebcamInformation.Webcam"/>

### WebcamInformation.Webcam



| Field | Type | Label | Description |
| ----- | ---- | ----- | ----------- |
| webcam_id | [string](#string) |  |  |
| available_modes | [string](#string) | repeated |  |





 

 

 


<a name="oak.platform.Webcam"/>

### Webcam
Manage streams from webcams connected to the host.

The &#39;webcam&#39; module must be activated before these RPCs are available.

The ports between 9000 and 9999 inclusive are reserved for
starting webcam streams.

&#39;webcam_id&#39; values come from serial numbers reported by the
webcams themselves.

| Method Name | Request Type | Response Type | Description |
| ----------- | ------------ | ------------- | ------------|
| Info | [.google.protobuf.Empty](#google.protobuf.Empty) | [WebcamInformation](#google.protobuf.Empty) | Lists available webcams and the modes (resolution and framerate) they support |
| StartStream | [StreamRequest](#oak.platform.StreamRequest) | [JpgStream](#oak.platform.StreamRequest) | A webcam can only have one stream at a time and a port can only be used for one stream at a time. |
| StopStream | [StreamRequest](#oak.platform.StreamRequest) | [.google.protobuf.Empty](#oak.platform.StreamRequest) | Stops a previously started stream from a specified camera |

 



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

