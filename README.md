# Nordic-MPM-Health-Devices
Support for the Metric Packet Model (MPM) Health Devices on Nordic platforms

This respository contains code that runs on the Nordic nRF52840 and nRF51 DKs. The code that runs on the nRF52840 DK should also run without issue on the nRF52 DK though it has not been tested.

Unlike the existing Bluetooth SIG health device profiles, the Metric Packet Model is generic and all health devices are supported by a single specification. The MPM is based upon the IEEE 11073 20601 Domain Information Model Objects though in a considerably simplified form. It is not necessary to understand the 20601 standard to work with the MPM. However, use of the MPM requires the understanding of the Medical Device Code (MDC) system and Mder Floats. The use of codes is totally foreign to the BT-SIG profiles but some of the profiles do use Mder Floats. Mder Floats are use to preserve precision.

The Bluetooth implementation is about as simple as it can get. GATT is used simply as a tunnel. The client sends commands to the server in one characteristic and the server notifies responses through a second characteristic. The exchange is completely synchronous. The endpoints only need to support descriptor and characteristic writes and indications and notifications. There is no need for the server to persist data in its server data tables but the Nordic SoftDevice will do that anyways. Only SoftDevice is used for the Bluetooth.

This MPM standard could be supported by any reliable transport.

## Repository Contents
The Nordic SDKs for nRF52 and nRF51 can be freely downloaded from https://www.nordicsemi.com/Products/Development-software/nRF5-SDK/Download#infotabs. This repository only contains code that is mean to be inserted into the nRF5_SDK_17.0.2_d674dde\examples\ble_peripheral or nrf_SDK_12.3.0\examples\ble_peripheral directory. Projects have been made for Segger Embedded Studio (which is free for development on Nordic platforms) and Keil. For the nRF51 projects only Keil projects are provided. However, the nRF51 project builds are small enough that one can use the size-limited free version.

