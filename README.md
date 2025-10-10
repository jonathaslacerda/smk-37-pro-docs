# M-VAVE SMK-37 PRO

## About

SMK 37 Pro is a MIDI keyboard master controller with a FM engine sound source compatible with Yamaha DX7 tone generator.

[https://www.m-vave.com/productinfo/1431195.html](https://www.m-vave.com/productinfo/1431195.html)

Documentation repository for M-Vave SMK 37 Pro

## Official Docs

* <a href="https://www.cuvave.com/productinfo/1431195.html" target="_blank">Product Page - SMK-37 Pro</a>
* [User Manual](manual/smk-37-pro-user-manual.pdf)
* [DAW Setup Manual](manual/smk-37-pro-daw-setup-manual.pdf)

## Hardware

* SoC JieLi AC7911B8? ([EdCo](https://www.sequencer.de/synthesizer/threads/m-vave-smk-37-pro-midi-controller-mit-eingebauter-dx7-engine-und-sequenzer.175956/page-3#post-2980924))
* SoC JieLi C108221-11B8? ([LarsLinux93](https://gist.github.com/probonopd/18b3ed65a69d0229eb630c47d7e316dc?permalink_comment_id=5739103#gistcomment-5739103))
  * [https://kagaimiq.github.io/jielie/chips/](https://kagaimiq.github.io/jielie/chips/) 
  * <a href="https://www.axtekic.com/web/uploads/file/20230313/gNZPgyZMJ87VB3CB0873B102SR6868n8.pdf" target="_blank">Datasheet</a>
  * 32-bit RISC CPU
    * Double core RISC 32-bit CPU(Support FPU)
    * 24KB D-Cache 6 way, 32KB I-Cache 8way
    * DC-320MHz operation
    * 128 Vectored interrupts
    * Four Levels interrupt priority

## Specifications

* Five colors available: White, Black, Pink, Red and Full Black
* 37 Keys with velocity-sensitive
* 16 RGB backlight pads with velocity and aftertouch
* 1.54" LCD Display
* Pitch and modulation wheels
* Eight 360-degree rotary encoders
* Four faders
* Step sequencer, smart chord, arpeggiator and note repeat function
* MIDI TRS Out Type A
* MIDI and Audio interface over USB C
* Stereo audio output (TRS)
* 1x sustain/expression 6.35mm (1/4") Pedal input standard jack
* MIDI over bluetooth 5.0
* 2000mAh battery
* Windows/MacOS/iOS/iPadOS/Android compatible
* Dimensions: TO-DO
* In the box: SMK 37 Pro, USB C -> USB A Cable, User manual

## Images

[Official and web images](images/IMAGES.md)

## Videos

<a href="https://www.youtube.com/playlist?list=PLYwLyF01evmMiaq1pv3QuYgvn-m5aVVDD" target="_blank">Official Youtube Playlist</a>

## Internal Synthesis Engine

*# FM Synth 
    * Six FM Operators, fully compatible with Yamaha DX7 MK1 (with some issues and glitches)
    * Feedback
    * 32 algorythm
    * Mono/Poly
    * FX: Cutoff, distortion, reverb, delay
* FX
    * Cutoff, distortion, reverb, delay
* Polyphony: 12 notes?

## Software and Apps

* Device Editor
  * [MidiSuite for Windows](https://yms-file-store.oss-cn-hongkong.aliyuncs.com/software/pc/MidiSuite.zip)
  * [MidiSuite for MacOS](https://yms-file-store.oss-cn-hongkong.aliyuncs.com/software/pc/MidiSuite.dmg)
  * <a href="https://apps.apple.com/us/app/midi-suite/id6737530581" target="_blank">MidiSuite for iOS/ipadOS</a>
  * [MidiSuite for Android](https://resource.m-vave.com/software/app/MidiSuite.apk)
* Firmware Upgrade
  * [M-Upgrade for Windows](https://yms-file-store.oss-cn-hongkong.aliyuncs.com/software/pc/M-UPGRADE.zip)
  * [M-Upgrade for MacOS](https://yms-file-store.oss-cn-hongkong.aliyuncs.com/software/pc/M-UPGRADE.dmg)
* Bluetooth MIDI Connector
  * [Sinco Connector for Windows](https://yms-file-store.oss-cn-hongkong.aliyuncs.com/software/pc/Sinco_Connector.exe)  

## Firmware ([thanks to probonopd](https://gist.github.com/probonopd/18b3ed65a69d0229eb630c47d7e316dc))

[Firmware versions](firmware/FIRMWARE.md)

## Known bugs and errors/issues

* Some latency found and appears to be related to power saving (not fixed until firmware 1.10 (v13)

## Hacking ([Thanks to probonopd](https://gist.github.com/probonopd/18b3ed65a69d0229eb630c47d7e316dc))

The firmware update file has the extension `.fwsc` and contains strings that make it seem probable that it uses a scheme similar (or identical) to what is described in [https://kagaimiq.github.io/jielie/datafmt/newfw.html](https://kagaimiq.github.io/jielie/datafmt/newfw.html).

```
git clone https://github.com/kagaimiq/jl-misctools
python3 -m pip install crcmod
python3 jl-misctools/firmware/fwunpack_newfw.py /mnt/c/Users/User/Downloads/*fwsc
#
# /mnt/c/Users/User/Downloads/SMK-37 Pro_012.fwsc
#

--- UFW file ---
 chip name: "AC791N"
Firmware base is at @0
  Burner size....: 544
  VID............: b'0.01'
  Flash size.....: $0FF000
  FS version.....: 16
  Block alignment: 16
  Special option.: $FF
  PID............: b'AC791N_STORY\xff\xff\xff\xff'
(top) <JLFS Entry @00000020 - 71C8 @000000A0/000000A0 (     14384/     14384) - 00/00 / 0 -- "uboot.boot">
(top) <JLFS Entry @00000040 - 70D5 @000038D0/000038D0 (       699/       699) - 02/80 / 0 -- "isd_config.ini">
Firmware chipkey from isd_config.ini: 980F
(top) <JLFS Entry @00000060 - FFFF @00004000/00004000 (4294967295/4294967295) - 81/FF / 0 -- "app_dir_head">
(top) <JLFS Entry @00000080 - FFFF @000FF000/000FF000 (      4096/      4096) - 12/01 / 65535 -- "key_mac">
Using chipkey: $980F
(App Area Head) <JLFS Entry @00004000 - BC2A @02000120/00004020 (    616499/    616467) - 83/FF / 0 -- "app_area_head">
Entry point address: 0x2000120
(App) <JLFS Entry @00004020 - CB2D @00000120/00004120 (    615828/    615828) - 82/FF / 0 -- "app.bin">
(App) <JLFS Entry @00004040 - 2E75 @000966B4/0009A6B4 (       383/       383) - 82/FF / 0 -- "cfg_tool.bin">
(App) <JLFS Entry @00004060 - FFFF @0009C000/000A0000 (    147456/    147456) - 12/81 / 0 -- "VM">
(App) <JLFS Entry @00004080 - FFFF @00000000/00004000 (    638976/    638976) - 92/82 / 0 -- "PRCT">
(App) <JLFS Entry @000040A0 - FFFF @000C0000/000C4000 (      4096/      4096) - 92/82 / 0 -- "BTIF">
(App) <JLFS Entry @000040C0 - FFFF @000C1000/000C5000 (      4096/      4096) - 92/81 / 0 -- "USRTRIM">
(App) <JLFS Entry @000040E0 - FFFF @000C2000/000C6000 (    167936/    167936) - 92/81 / 0 -- "USRFLASH">
(App) <JLFS Entry @00004100 - FFFF @000F4000/000F8000 (     40960/     40960) - 92/81 / 1 -- "USR">
(Res) <JLFS Entry @0009A833 - ABBD @00000020/0009A853 (      2937/      2905) - 83/FF / 1 -- "cfg">
====> <JLFS Entry @0009A853 - 017D @00000040/0009A873 (      2873/      2873) - 82/FF / 1 -- "eq_cfg_hw.bin">
```

* Strings like `btstack_lowpwer_deal` possibly suggest https://github.com/Jieli-Tech/fw-AC63_BT_SDK/ (or similar) being used?
* Possbly JL_AC79_DevKit V1.0 is the development environment?
* https://doc.zh-jieli.com/AC79/zh-cn/master/board_description/board_overview/index.html
