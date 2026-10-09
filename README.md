# Mi8937 Builds

Unofficial LineageOS 23.2 for Xiaomi Mi8937. Initial phone testing is on Redmi 4X (santoni), running official LineageOS 23.2 before migration.

## Downloads

The initial ROM packages and standalone recovery are available in the [published release](https://github.com/unicastbg/mi8937-builds/releases/tag/mi8937-23.2-20261008).

Use the assets in [Releases](https://github.com/unicastbg/mi8937-builds/releases). GitHub's Source code archives are not ROM packages.

- One-time migration: `lineage-23.2-20261008-UNOFFICIAL-Mi8937-migration.zip`.
- Normal ROM: `lineage-23.2-20261008-UNOFFICIAL-Mi8937.zip`.
- Optional standalone recovery: `recovery.img`, for Mi8937 only.
- Verify each download against its matching `.sha256` file.

Never install Mi439 packages on these devices.

## Migration From Official LineageOS 23.2

Back up important data first. These instructions are for an existing official 23.2 installation, not stock MIUI or an older Android release.

1. In recovery, select Apply update > Apply from ADB and sideload the migration ZIP.
2. Wait for status 0, boot Android once and confirm your apps and files are present.
3. Promptly return to recovery and sideload the normal ZIP.
4. Wait for status 0, then reboot Android.

Do not wipe or format data, unlock/relock the bootloader or repeat migration on an existing community normal build. Migration temporarily relaxes package-signature checks; the normal ROM removes that code and installs community recovery.

Official recovery may show error 21 for our unfamiliar signing certificate during the initial manual sideload. Verify source and checksum before accepting an expected signature warning. Stop for a device mismatch, nonzero final status or unexpected errors. Error 21 during unattended OTA is a failure.

## Updates and Testing

The owner reports migration boot and normal installation with status 0 and no data loss on one Redmi 4X. Other Mi8937 models, hardware functions and add-ons are not comprehensively validated. Google Apps, microG and Magisk preservation are not yet confirmed. Keep backups; data preservation is not guaranteed.

The normal ROM points Updater to a [separate Mi8937 feed](https://unicastbg.github.io/mi439-ota/Mi8937-23.2.json), hosted in the existing OTA repository. It is currently empty. Automatic OTA on Redmi 4X has not yet been phone-tested. Once validated, future normal releases will use Updater without repeating migration.

Packaging checks passed for ZIP integrity, whole-file OTA signatures, APEX signatures, duplicate-free trusted recovery certificates, recovery installation and absence of an OTA wipe request. Mi8937 upstream disables AVB; no claim of AVB protection is made.

Android security patch level: `2026-09-01`. Upstream platform updates do not guarantee current patches for all old proprietary firmware or vendor components.

## Sources

- [Exact kernel source used](https://github.com/LineageOS/android_kernel_xiaomi_msm8937/tree/704f6f08135c39728fcbe6f94b3956d911bb1801), branch `lineage-23.2`; no local kernel-source changes.
- [Mi8937 device tree](https://github.com/LineageOS/android_device_xiaomi_Mi8937/tree/1d087f13f1027de6b110ae3f2a24f27de5d841a8).
- [Shared device tree](https://github.com/LineageOS/android_device_xiaomi_mithorium-common/tree/2639cd7377cbd6b6ecf6f5317637c3faca96f86c).
- The release's `build-manifest.xml` records the resolved source revisions.

ROM ZIPs are release assets, not committed to Git. Private signing keys are never published.
