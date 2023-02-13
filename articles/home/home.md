# Home diagrams

## Desk setup

A logical view of my desk. A goal is to keep personal and work setups nearby, but physically separated.

```mermaid
graph LR
    Desktop
    Monitor0
    Monitor1
    Quest2
    Keyboard0
    Mouse1

    Desktop -->|dp| Monitor0
    Desktop -->|dp| Monitor1
    Desktop -->|usb| Keyboard0
    Desktop -->|usb| Mouse0
    Desktop -.->|3.5mm| Headphones
    Desktop -->|usb| Quest2
    Monitor0 -->|3.5mm| Desktop

    Subwoofer
    SpeakerL
    SpeakerR
    Microphone
    Buds
    IfRecord
    Headphones
    DAC
    Subwoofer -->|xlr| SpeakerL
    Subwoofer -->|xlr| SpeakerR
    Desktop -->|spdif| DAC
    DAC -->|xlr| Subwoofer
    Desktop -->|usb| IfRecord
    Desktop -.->|bt| Buds
    IfRecord -->|xlr| Microphone

    subgraph Corp
        CorpHeadset
        CorpLaptop
        Keyboard1
        Mouse1
        Monitor2
        CorpLaptop -->|usb| Monitor2
        Monitor2 -->|usb| Keyboard1
        CorpLaptop -.->|bt| Mouse1
        Monitor2 -->|usb| CorpHeadset
    end

    AirSensor
    Natsumi["MiniPC\nNatsumi"]
    AirSensor -.->|wifi| Natsumi

    NintendoSwitch
    NintendoSwitch -->|hdmi| Monitor0

    subgraph Plant
        Plant0
        Plant1
        Plant2
    end
```
    
## Network

The goal is to keep things as simple as possible.

```mermaid
graph LR
  FibrePoint["Fibre termination point"] -->|fibre| ONT["Optical Network Terminal\nONT"]
  ONT -->|eth| EdgeRouter
  EdgeRouter -->|eth| WAPLiving
  EdgeRouter -->|eth| WAPHallway
  EdgeRouter -->|eth| MiniPC[MiniPC\nNATSUMI]
  EdgeRouter -->|eth| NAS[NAS\nATHENA]

  subgraph WAP
    WAPLiving
    WAPHallway
  end

  subgraph WiFi
    Desktop
    AirSensor
    CorpLaptop
    Phone
    Others
  end
  WAP -.->|"2.4GHz + 5GHz\nHermes"| WiFi

  EdgeRouter -.->|"eth, VLAN 10 (inactive)"| IPTV
```
