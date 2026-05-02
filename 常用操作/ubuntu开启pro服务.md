
# ubuntu 开启 pro 服务

```bash
pro attach <token>
```

## ubuntu 未开启 pro 服务

```bash
# pro status --all
SERVICE          AVAILABLE  DESCRIPTION
anbox-cloud      yes        Scalable Android in the cloud
cc-eal           no         Common Criteria EAL2 Provisioning Packages
esm-apps         yes        Expanded Security Maintenance for Applications
esm-apps-legacy  no         Expanded Security Maintenance for Applications on Legacy Instances
esm-infra        yes        Expanded Security Maintenance for Infrastructure
esm-infra-legacy no         Expanded Security Maintenance for Infrastructure on Legacy Instances
fips             no         NIST-certified FIPS crypto packages
fips-preview     no         Preview of FIPS crypto packages undergoing certification with NIST
fips-updates     yes        FIPS compliant crypto packages with stable security updates
landscape        yes        Management and administration tool for Ubuntu
livepatch        yes        Canonical Livepatch service
realtime-kernel  yes        Ubuntu kernel with PREEMPT_RT patches integrated
ros              no         Security Updates for the Robot Operating System
ros-updates      no         All Updates for the Robot Operating System
usg              yes        Security compliance and audit tools

This machine is not attached to an Ubuntu Pro subscription.
See https://ubuntu.com/pro
```

## ubuntu 开启 pro 服务后显示

```bash
# pro status --all
SERVICE          ENTITLED  STATUS       DESCRIPTION
anbox-cloud      yes       disabled     Scalable Android in the cloud
cc-eal           yes       n/a          Common Criteria EAL2 Provisioning Packages
esm-apps         yes       enabled      Expanded Security Maintenance for Applications
esm-infra        yes       enabled      Expanded Security Maintenance for Infrastructure
fips             yes       n/a          NIST-certified FIPS crypto packages
fips-preview     yes       n/a          Preview of FIPS crypto packages undergoing certification with NIST
fips-updates     yes       disabled     FIPS compliant crypto packages with stable security updates
landscape        yes       disabled     Management and administration tool for Ubuntu
livepatch        yes       enabled      Canonical Livepatch service
realtime-kernel  yes       disabled     Ubuntu kernel with PREEMPT_RT patches integrated
├ generic        yes       disabled     Generic version of the RT kernel (default)
├ intel-iotg     yes       n/a          RT kernel optimized for Intel IOTG platform
└ raspi          yes       n/a          24.04 Real-time kernel optimised for Raspberry Pi
ros              yes       n/a          Security Updates for the Robot Operating System
ros-updates      yes       n/a          All Updates for the Robot Operating System
usg              yes       disabled     Security compliance and audit tools

Enable services with: pro enable <service>

     Account: ********************
Subscription: Ubuntu Pro - free personal subscription

```

## 更新软件包举例

```bash
# apt list --upgradable
Listing... Done
iproute2/noble-updates 6.1.0-1ubuntu6.3 amd64 [upgradable from: 6.1.0-1ubuntu6.2]
libavcodec60/noble-apps-security 7:6.1.1-3ubuntu5+esm7 amd64 [upgradable from: 7:6.1.1-3ubuntu5]
libavutil58/noble-apps-security 7:6.1.1-3ubuntu5+esm7 amd64 [upgradable from: 7:6.1.1-3ubuntu5]
libswresample4/noble-apps-security 7:6.1.1-3ubuntu5+esm7 amd64 [upgradable from: 7:6.1.1-3ubuntu5]
libzvbi-common/noble-apps-security 0.2.42-2ubuntu0.24.04.1~esm1 all [upgradable from: 0.2.42-2]
libzvbi0t64/noble-apps-security 0.2.42-2ubuntu0.24.04.1~esm1 amd64 [upgradable from: 0.2.42-2]
openssh-client/noble-updates,noble-security 1:9.6p1-3ubuntu13.16 amd64 [upgradable from: 1:9.6p1-3ubuntu13.15]
openssh-server/noble-updates,noble-security 1:9.6p1-3ubuntu13.16 amd64 [upgradable from: 1:9.6p1-3ubuntu13.15]
openssh-sftp-server/noble-updates,noble-security 1:9.6p1-3ubuntu13.16 amd64 [upgradable from: 1:9.6p1-3ubuntu13.15]
thermald/noble-updates 2.5.6-2ubuntu0.24.04.5 amd64 [upgradable from: 2.5.6-2ubuntu0.24.04.3]
```

✅ 可以直接正常升级的包（5个）
这些包来自标准的 noble-updates/noble-security 源，不需要 Ubuntu Pro 就可以直接安装：

软件包 版本变化
iproute2 6.1.0-1ubuntu6.2 → 6.1.0-1ubuntu6.3
openssh-client 1:9.6p1-3ubuntu13.15 → 1:9.6p1-3ubuntu13.16
openssh-server 1:9.6p1-3ubuntu13.15 → 1:9.6p1-3ubuntu13.16
openssh-sftp-server 1:9.6p1-3ubuntu13.15 → 1:9.6p1-3ubuntu13.16
thermald 2.5.6-2ubuntu0.24.04.3 → 2.5.6-2ubuntu0.24.04.5
🔐 需要 Ubuntu Pro 才能升级的包（5个）
这些包的源是 noble-apps-security，属于 esm-apps 服务范围，需要绑定 Ubuntu Pro 订阅才能安装：

软件包 版本变化 说明
libavcodec60 7:6.1.1-3ubuntu5 → 7:6.1.1-3ubuntu5+esm7 FFmpeg 音视频编解码库
libavutil58 7:6.1.1-3ubuntu5 → 7:6.1.1-3ubuntu5+esm7 FFmpeg 工具库
libswresample4 7:6.1.1-3ubuntu5 → 7:6.1.1-3ubuntu5+esm7 FFmpeg 音频重采样库
libzvbi-common 0.2.42-2 → 0.2.42-2ubuntu0.24.04.1~esm1 VBI 数据解码库（公共文件）
libzvbi0t64 0.2.42-2 → 0.2.42-2ubuntu0.24.04.1~esm1 VBI 数据解码库（核心库）
