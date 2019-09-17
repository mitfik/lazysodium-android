<br>

<p align="center"><img width="260" style="float: center;" style="display: inline;" src="https://filedn.com/lssh2fV92SE8dRT5CWJvvSy/lazycode/lazysodium/large_logo.png" /></p>
  
<br>
  
# Lazysodium for Android
  
Lazysodium is a **complete** Android implementation of the [Libsodium](https://github.com/jedisct1/libsodium) library that provides developers with a **smooth and effortless** cryptography experience.
  
[![Download](https://api.bintray.com/packages/terl/lazysodium-maven/lazysodium-android/images/download.svg) ](https://bintray.com/terl/lazysodium-maven/lazysodium-android/_latestVersion)


## Why Lazysodium
We created Lazysodium because we really wanted a solid Libsodium compatible Java/Android library that would just work without fuss. We were exasperated and annoyed with current Libsodium implementations as some of them were just poorly maintained and poorly architected.

You can find more info [here](https://docs.lazycode.co/lazysodium/about-1).

## Used by

| **Name** | **Short description** | **Android** | **Java** |
| :--- | :--- | :--- | :--- |
| [**Threema \(SaltyRTC\)**](https://github.com/saltyrtc/saltyrtc-client-java) | Threema is a global end-to-end encrypted chatting app and _SaltyRTC_ is their protocol for encryption. | ✓ | ✓ |
| [**PayPay**](https://github.com/paypayue/AndroidPaymentSDK) | CardPaymentSDK is a card payments library to make payments through several payment methods painless. It uses [PayPay](https://paypay.pt/paypay/) as an endpoint to establish a payment security channel. | ✓ | ✗ |
| [**RDACAA**](https://gitlab.com/MSP_EC/rdacaa/tree/88-cierre-del-mes-atenciones-por-usuario)| Used by the government of Ecuador's Ministry of Health to encrypt and sign a list of ambulatory care and consultations. | ✗ | ✓ |
| [**E3DB**](https://tozny.com/e3db/) | An encrypted NoSQL database designed from the ground-up for user privacy and security. | ✓ | ✓ |
| [**ADAMANT**](https://adamant.im/) | The most private messenger possible. Your device does not store any info. It directly interacts with the blockchain, where every byte is fully-encrypted. | ✓ | ✗ |
| [**Kepler**](https://github.com/Quackster/Kepler) | A small TCP server written in Java powered by Netty, an asynchronous networking library. | ✗ | ✓ |
| [**Regen Ledger**](https://www.regen.network/) | A global marketplace & contracting platform for Earth's ecosystem assets, services, and data. | ✗ | ✓ |
| [**Tezos**](https://github.com/LMilfont/TezosJ-plainjava) | The TezosJ SDK library enables plain Java developers to create applications that communicates with Tezos blockchain. | ✗ | ✓ |
| [**Exonum**](https://github.com/exonum/exonum-java-binding) | Exonum Java Binding is a framework for building blockchain applications in Java, powered by Exonum. | ✗ | ✓ |
| [**Paseto**](https://github.com/atholbro/paseto) | Java Implementation of Platform-Agnostic Security Tokens. | ✗ | ✓ |
| [**Recordo**](https://recordo.co) | A super secure diary/journal that provides end to end encryption. | ✓ | ✓ |


## Features
You can find an up-to-date feature list [here](https://docs.lazycode.co/lazysodium/about-1/features).

## Quick start

This is by no means a comprehensive introduction to Lazysodium. Please view the [official documentation](https://docs.lazycode.co/lazysodium/usage/installation) for a more comprehensive guide.

### 1. Install
Install by adding the bintray repository and the dependency. For Maven users, please see [here](https://docs.lazycode.co/lazysodium/usage/installation).

```groovy
// Top level build file
repositories {
    maven {
        url  "https://dl.bintray.com/terl/lazysodium-maven"
    }
}

// Add to dependencies section
dependencies {
    implementation "com.goterl.lazycode:lazysodium-android:VERSION_NUMBER@aar"
    implementation 'net.java.dev.jna:jna:4.5.1@aar'
}
```

Substitute `VERSION_NUMBER` for the version in this box:

[![Download](https://api.bintray.com/packages/terl/lazysodium-maven/lazysodium-android/images/download.svg) ](https://bintray.com/terl/lazysodium-maven/lazysodium-android/_latestVersion)


### 2. Let's go!

You can now initialise and start encrypting! **Please note** that this library follows the official [libsodium docs](https://download.libsodium.org/doc/) closely. You need to use those docs to help you find the functions you need.

```java
// Let's initialise LazySodium, perhaps in an Application class somewhere
LazySodiumAndroid lazySodium = new LazySodiumAndroid(new SodiumAndroid());

// Now you can cast to an interface so that our
// IDE picks up and intelligently loads up the correct methods. 
SecretBox.Native secretBoxNative = (SecretBox.Native) lazySodium;
SecretBox.Lazy secretBoxLazy = (SecretBox.Lazy) lazySodium;

// The first one is Lazysodium's Native implementation which
// is just like libsodium's native C function but with tiny enhancements
// to make your life easier.
secretBoxNative.cryptoSecretBoxKeygen(key);
// Convert key to string and save to DB

// This one is Lazysodium's Lazy implementation which makes
// your work with cryptography super easy.
String key = secretBoxLazy.cryptoSecretBoxKeygen();
```

In the above code there are two ways you can use Lazysodium. The first way is through the `Native` interface. The second is through the `Lazy` interface. 

### 3. You decide

Every project is different, you may need to use lower-level APIs to achieve the control you need so you use the `Native` interface. Or alternatively you just don't want to deal with the details so you stick to the `Lazy` interface.

Every interface you can cast to is helpfully all in [one directory](https://github.com/terl/lazysodium-java/tree/20c9a43aac6be5f23209b15870a8cbf73e26ab22/src/main/java/com/goterl/lazycode/lazysodium/interfaces) so you can easily pick the functions you need. This isolates your code and prevents you from making mistakes.

**Important:** If possible, please stick to using either the `Native` *or* the `Lazy` interface. The reason for this is that the `Lazy` interface normally converts everything to hexadecimal whereas the `Native` interface assumes everything is non-hexadecimal. If you don't know what you're doing, you could end up making mistakes.


## Documentation

See our [official documentation](https://docs.lazycode.co/lazysodium) to get started.

## Apps

You can preview some of the features in our free Lazysodium app available on Google Play:

<a href='https://play.google.com/store/apps/details?id=com.goterl.lazycode.lazysodium.example&pcampaignid=MKT-Other-global-all-co-prtnr-py-PartBadge-Mar2515-1'><img alt='Get it on Google Play' src='https://play.google.com/intl/en_gb/badges/images/generic/en_badge_web_generic.png' width="140"/></a>


## Lazysodium for Java
We also have a Java implementation available at [Lazysodium for Java](https://github.com/terl/lazysodium-java). It has the same API as this library so you can share code easily!


---

<a href="https://terl.co"><img width="100" style="float: left: display: inline;" src="https://filedn.com/lssh2fV92SE8dRT5CWJvvSy/terl.png" /></a>

Created by [Terl](https://terl.co).
