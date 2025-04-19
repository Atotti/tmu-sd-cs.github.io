---
layout: staff_member
title: Nobutaka Ono Laboratory
copyright_year: 2020
staff_id: ono
staff_name: Nobutaka Ono
staff_title: Professor
staff_image: ono_prof.jpg
lang: "en"
ref: "staff-ono"
specialties:
- Microphone Array
- Sound Source Separation
- Acoustic Scene Recognition
- Time-Frequency Analysis
- Acoustic Signal Processing
description: Sound is an important medium containing diverse information, and we communicate through speech, enjoy music, and perceive various situations around us through sound on a daily basis. The Ono Laboratory aims to realize advanced sound information processing that is similar to or beyond human capabilities, and conducts research on signal processing and information processing for sound, such as speech and music. For example, we are working on the following research topics.
links:
- title: Laboratory Website
  url: http://www.comp.sd.tmu.ac.jp/onolab/
---


### Fast Blind Source Separation

In real environments, various sounds are mixed together, but for example, speech recognition does not work well when noise or multiple voices are mixed. The technology to decompose such mixed sounds into individual sounds without prior information is called blind source separation. Conventional techniques had the problem of high computational cost, but the Ono Laboratory devised the world's fastest algorithm called Auxiliary-function-based Independent Vector Analysis (AuxIVA) in 2011, and further implemented it as an iPhone app to demonstrate its speed.

In recent years, we have also been working on algorithm development and system implementation for low-latency real-time processing, aiming for hearing aid applications.

<figure class="center w70">
  <img src="/image/ono_01.jpg" alt="">
  <figcaption>Fast blind source separation running on iPhone</figcaption>
</figure>


### Asynchronous Distributed Microphone Array

A system that uses multiple microphones to acquire and process spatial information of sound is called a microphone array. In microphone arrays, the minute time differences between multiple microphone signals (for example, about 0.1ms) are important clues for sound source localization and separation, so synchronous recording with multiple microphones was essential. On the other hand, there are many devices with recording capabilities (PCs, smartphones, etc.) around us. We are researching new signal processing technologies for array signal processing with such asynchronous recording devices. For example, we aim for applications such as having meeting participants record the meeting with their own smartphones, and after uploading to the cloud after the meeting, the signals are automatically synchronized, source separated, speech recognized, and minutes are sent by email.


### Acoustic Sensing Based on Sound-to-Light Conversion and Video Cameras

We are beginning research on a new acoustic sensing method that combines sensor nodes that illuminate LEDs according to sound intensity with cameras, using the camera as an ultra-multi-channel acoustic device. Although spectral information of sound cannot be obtained, it is possible to acquire spatially wide-ranging information at once, and since it can utilize security cameras and surveillance cameras, we believe it can be widely applied to environmental recognition and anomaly detection by sound. We have already developed an inexpensive and small device that operates independently with a battery.
