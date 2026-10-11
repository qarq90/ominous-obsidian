## Compare Infrastructure-based Network and Adhoc Network.

| Factor             | Infrastructure-based Network | Adhoc Network               |
| ------------------ | ---------------------------- | --------------------------- |
| Technology         | Access points, switches      | Peer-to-peer wireless       |
| Structure          | Centralized, fixed           | Decentralized, dynamic      |
| Working            | Via base station             | Direct device communication |
| Data Rate          | Generally higher             | Generally lower             |
| Feature Introduced | Central management           | Self-configuring nodes      |
| Security           | Stronger authentication      | Vulnerable to attacks       |
| Interference       | Managed centrally            | Higher due to hops          |
| Complexity         | Lower for nodes              | Higher routing complexity   |
| Limitation         | Infrastructure dependent     | Scalability issues          |
| Applications       | Enterprise Wi-Fi             | Military, disaster relief   |

---

## Compare Frequency Hopping Spread Spectrum (FHSS) and Direct Sequence Spread Spectrum (DSSS).

| Factor             | FHSS                              | DSSS                               |
| ------------------ | --------------------------------- | ---------------------------------- |
| Full form          | Frequency Hopping Spread Spectrum | Direct Sequence Spread Spectrum    |
| Technology         | Carrier frequency hopping         | Pseudo-noise coding                |
| Structure          | Narrowband, frequency switching   | Wideband, continuous signal        |
| Working            | Changes frequencies rapidly       | Multiplies data with chipping code |
| Data Rate          | Lower (per channel)               | Higher                             |
| Feature Introduced | Frequency agility                 | Code division                      |
| Security           | Good against eavesdropping        | Better anti-jamming                |
| Interference       | Avoids narrowband interference    | Spreads interference energy        |
| Complexity         | Moderate (synchronization needed) | Higher (code generation)           |
| Limitation         | Low throughput                    | Near-far problem                   |
| Applications       | Bluetooth, cordless phones        | GPS, CDMA, Wi-Fi                   |

---

## Compare FDMA, TDMA and CDMA.

| Factor | FDMA | TDMA | CDMA |
| --- | --- | --- | --- |
| Full form | Frequency Division Multiple Access | Time Division Multiple Access | Code Division Multiple Access |
| Technology | Separate frequency bands | Separate time slots | Unique code sequences |
| Structure | Continuous transmission | Pulsed transmission | Simultaneous transmission |
| Working | Each call on different freq | Each call in time slice | All on same freq/time |
| Data Rate | Fixed per channel | Varies per slot | Variable, soft capacity |
| Feature Introduced | Frequency separation | Time sharing | Code separation |
| Security | Low (easy to tap) | Moderate | High (code unknown) |
| Interference | Adjacent channel | No within system | All users interfere |
| Complexity | Low (simple filters) | Moderate (sync needed) | High (power control) |
| Limitation | Inefficient use of spectrum | Needs guard times | Near-far problem |
| Applications | Analog cellular (1G) | GSM (2G) | 3G, GPS |

---

## Differentiate between GSM and UMTS.

| Factor | GSM | UMTS |
| --- | --- | --- |
| Full form | Global System for Mobile | Universal Mobile Telecom System |
| Technology | TDMA + FDMA | W-CDMA |
| Structure | Circuit-switched | Circuit + Packet |
| Working | Time/freq slots | Code division |
| Data Rate | 9.6 – 171 kbps | 384 kbps – 2 Mbps |
| Feature Introduced | SIM card, roaming | High-speed data |
| Security | Moderate (A5/1 cipher) | Stronger (A5/3) |
| Interference | Lower (guard bands) | Higher (self-interference) |
| Complexity | Lower | Higher |
| Limitation | Low data rate | Needs more bandwidth |
| Applications | Voice, SMS, GPRS | Video calls, mobile web |

---

## Compare 1G to 5G mobile standards.

| Factor | 1G | 2G | 3G | 4G | 5G |
| --- | --- | --- | --- | --- | --- |
| Full form | First Generation | Second Generation | Third Generation | Fourth Generation | Fifth Generation |
| Technology | Analog (AMPS) | Digital (GSM, CDMA) | W-CDMA, UMTS | LTE, WiMAX | NR (mmWave, sub-6) |
| Structure | Analog cellular | TDMA/FDMA | Packet-switched | All-IP | Cloud-native |
| Working | Frequency division | Time/freq slots | Code + packet | OFDMA | OFDMA + beamforming |
| Data Rate | 2.4 kbps | 64–171 kbps | 2 Mbps – 42 Mbps | 100 Mbps – 1 Gbps | 1–20 Gbps |
| Feature Introduced | Mobile voice | SMS, digital encryption | Mobile internet | Video streaming | URLLC, mMTC |
| Security | Very weak | Moderate | Strong | Stronger | Enhanced privacy |
| Interference | High | Medium | Medium | Low | Very low |
| Complexity | Low | Medium | High | Very high | Extremely high |
| Limitation | No data | Low speed | High latency | Complex MIMO | Limited coverage |
| Applications | Voice calls | Voice + SMS | Web browsing | HD video | IoT, autonomous cars |

---

## Compare IEEE 802.11 and IEEE 802.16.

| Factor | IEEE 802.11 | IEEE 802.16 |
| --- | --- | --- |
| Full form | Wireless LAN standard | Wireless MAN standard |
| Technology | CSMA/CA | OFDM, QoS scheduling |
| Structure | Infrastructure or adhoc | Base station + subscribers |
| Working | Contention-based access | Scheduled access |
| Data Rate | 11 Mbps – 9.6 Gbps | Up to 1 Gbps (fixed) |
| Feature Introduced | Wi-Fi | WiMAX |
| Security | WEP, WPA, WPA3 | AES, PKM |
| Interference | High (unlicensed band) | Lower (licensed possible) |
| Complexity | Low to moderate | Higher |
| Limitation | Short range (~100 m) | Higher cost, less mobility |
| Applications | Home, office WLAN | Backhaul, rural broadband |

---

## Compare VANET and MANET.

| Factor | VANET | MANET |
| --- | --- | --- |
| Full form | Vehicular Adhoc Network | Mobile Adhoc Network |
| Technology | Dedicated Short Range Comm (DSRC) | Bluetooth, Wi-Fi direct |
| Structure | Highly dynamic, road-based | Random mobility |
| Working | Vehicle-to-vehicle (V2V) | Peer-to-peer |
| Data Rate | 3–27 Mbps (DSRC) | 1–100 Mbps |
| Feature Introduced | Roadside units (RSUs) | Fully self-organizing |
| Security | Critical (safety) | Moderate |
| Interference | High (dense traffic) | Variable |
| Complexity | Very high (fast moving) | Moderate |
| Limitation | Regular disconnections | Limited battery/range |
| Applications | Collision warning, tolling | Disaster recovery, battlefields |

---

# Compare VANET and WSN.

| Feature                    | MANET                                        | WSN                                                            |
| -------------------------- | -------------------------------------------- | -------------------------------------------------------------- |
| **Full Form**              | Mobile Ad Hoc Network                        | Wireless Sensor Network                                        |
| **Node Type**              | Laptops, smartphones, tablets, PDAs          | Tiny sensor nodes (motes)                                      |
| **Node Mobility**          | High – nodes move freely                     | Low to moderate – sensors are often static                     |
| **Node Density**           | Low to moderate                              | High (hundreds to thousands of nodes)                          |
| **Power Supply**           | Rechargeable batteries (limited)             | Non-rechargeable batteries (very limited)                      |
| **Primary Function**       | General-purpose data communication           | Sensing, monitoring, and data collection                       |
| **Data Rate**              | High (1–100 Mbps)                            | Low (kbps to hundreds of kbps)                                 |
| **Processing Power**       | Moderate to high (smartphone-level)          | Very low (microcontroller-level)                               |
| **Memory**                 | Adequate (GBs)                               | Very limited (KB to MB)                                        |
| **Routing Protocol Focus** | Mobility management and link stability       | Energy efficiency and data aggregation                         |
| **Communication Pattern**  | Peer-to-peer, any-to-any                     | Many-to-one (nodes to sink/gateway)                            |
| **Node Address**           | Unique IP or MAC address                     | Often ID-based, not globally unique                            |
| **Cost per Node**          | High (expensive devices)                     | Very low (cheap sensors)                                       |
| **Typical Applications**   | Battlefield, disaster recovery, conferencing | Environmental monitoring, healthcare, agriculture, smart homes |
| **Security Threats**       | Eavesdropping, DoS, routing attacks          | Node tampering, data injection, physical capture               |
| **Scalability**            | Tens to hundreds of nodes                    | Hundreds to thousands of nodes                                 |

