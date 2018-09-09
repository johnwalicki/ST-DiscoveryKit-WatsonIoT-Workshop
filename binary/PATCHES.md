### System Workbench for STM32 / TrueSTUDIO
For software IDE downloads, see Slides 17 - 20 of the [STDevCon_5.2.2  Intro to ST Discovery Kit IoT Node and IBM Watson.pdf](../STDevCon_5.2.2%20%20Intro%20to%20ST%20Discovery%20Kit%20IoT%20Node%20and%20IBM%20Watson.pdf)

### Source Code Download
[X-CUBE-Watson IBM Watson software expansion for STM32Cube](https://www.st.com/content/st_com/en/products/embedded-software/mcus-embedded-software/stm32-embedded-software/stm32cube-expansion-packages/x-cube-watson.html)

### Binary Download
[B-L475E-IOT01_Watson_IoT_Cloud_1.0.2.bin](B-L475E-IOT01_Watson_IoT_Cloud_1.0.2.bin)

### Patches
WATSON_1.0.2.patch is a cumulative patch which must be applied on top of WATSON_1.0.1.patch

To apply a patch from the Project directory of the WATSON.1.0.0 release:
```
patch -p1 < WATSON_1.0.1.patch
patch -p1 < WATSON_1.0.2.patch
```

### Changelog:
- WATSON_1.0.2.patch - small fix which allows “Token” to be part of the token string.
- WATSON_1.0.1.patch - hard-code the Watson IoT root CA certificate
