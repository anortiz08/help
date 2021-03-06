---
layout: article
title: Set up two-step login with YubiKey
categories: [account-management]
featured: false
popular: false
tags: [two-step login, 2fa, two factor authentication, account, yubikey, yubi, yubico]
---

bitwarden supports two-step login via [YubiKey](https://www.yubico.com){:target="_blank"}. Any YubiKey that supports [OTP capabilities](https://www.yubico.com/products/yubikey-hardware/compare-yubikeys/){:target="_blank"} can be used. This includes all YubiKey 4 series devices as well as YubiKey NEO.

{% note %}
Due to platform limitations, YubiKeys cannot be used on all bitwarden applications. You should enable another two-step login provider so that you can access your account when YubiKeys cannot be used.

Supported platforms:

- Web vault on a device with a USB port that can accept your YubiKey.
- Browser extensions.
- Android on a device with [NFC capabilities](https://en.wikipedia.org/wiki/List_of_NFC-enabled_mobile_devices){:target="_blank"}. Read more [here](https://forum.yubico.com/viewtopic.php?f=26&t=1302){:target="_blank"}.
{% endnote %}

## Enable Two-step Login with YubiKey

{% warning %}
Two-step login can permanently lock you out of your account. It is very important that you write down and keep your [two-step login recovery code]({% link _articles/account/lost-two-step-device.md %}) in a safe place in the event that you lose access to your YubiKey.
{% endwarning %}

1. Log in to the web vault at <https://vault.bitwarden.com>
2. Click **Settings** on the sidebar. Click **Two-step Login** in the sub-menu that opens under **Settings**.  
3. Select the **YubiKey OTP Security Key** option and then type in your master password to continue.
   {% image two-step/yubikey/select.png %}
4. Follow the instructions shown:
   - Plug the YubiKey (NEO or 4 series) into your computer's USB port.
   - Select in the first empty Key input field.
   - Touch the YubiKey's button.
   
   Repeat this process for each YubiKey you wish to add to your account. You can add up to three YubiKeys to your account.
   {% image two-step/yubikey/config.png %}
5. If you are using a YubiKey that has NFC capabilities (YubiKey NEO), check the **One of my keys supports NFC** checkbox. This option enables the use of your YubiKey on Android devices that support NFC.
6. Click the **Enable** button. A green alert will appear at the top stating that two-step login has been enabled.
7. Click the **Close** button and confirm that the **YubiKey OTP Security Key** option now shows as **Enabled**.
   {% image two-step/yubikey/enabled.png %}

## Test

1. **IMPORTANT:** Ensure that you have copied down your [two-step login recovery code]({% link _articles/account/lost-two-step-device.md %}) in case something goes wrong.
2. Log out of the bitwarden web vault.
3. Log back into the bitwarden web vault. You should now be prompted with a YubiKey two-step login option. Insert your YubiKey and touch it's button to complete logging in.
4. Log out of and back in to any other bitwarden applications that you are using to confirm that two-step login via YubiKey is properly working. You will eventually be logged out automatically. If the application (or device) your are using does not support YubiKey you will be presented with other two-step login options that you have configured (if any).

   Web
   {% image two-step/yubikey/web.png %}

   Browser extension
   {% image two-step/yubikey/browser.png %}

   Android
   {% image two-step/yubikey/android.png %}

## Android

If you are having trouble getting the YubiKey NEO to work on your Android device, confirm the following:

1. You have checked the **One of my keys supports NFC** checkbox from step 5 above.
2. Your Android device [supports NFC](https://en.wikipedia.org/wiki/List_of_NFC-enabled_mobile_devices){:target="_blank"} and is [known to work properly](https://forum.yubico.com/viewtopic.php?f=26&t=1302){:target="_blank"} with YubiKey NEO.
3. You have NFC enabled on your Android device. Enable NFC by going to Android **Settings** &rarr; **More** and enable the **NFC** option.

If the YubiKey NEO can be used on your Android device you will be prompted with a YubiKey option while logging in to bitwarden. Simply place the YubiKey NEO on the back of your Android device near the NFC receiver. If you do not know where your NFC receiver is located, you may need to move it around some, trying different areas. Once bitwarden detects the YubiKey it will automatically validate and log you in.

