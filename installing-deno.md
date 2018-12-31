# 安装 Deno

## 获取 Deno 发布版程序

Deno 还在十分早期的开发阶段。 目前的发布版是 0.2.x，可以视为“勉强可用”，主要供开发者预览试用。 

要在 \*nix 系统中安装 Deno 发布版, 请运行以下命令：

```bash
curl -L https://deno.land/x/install/install.py | python
export PATH=$HOME/.deno/bin:$PATH
```

在 Windows 系统中安装时, 请在 Powershell 中运行以下命令:

```text
iex (iwr https://deno.land/x/install/install.ps1)
```

Deno 的安装过程由位于 [deno\_install](https://github.com/denoland/deno_install) 的脚本负责。如果你在安装过程中遇到任何问题，请到那里提交 issue。

## 编译 Deno 源码

如果你有心参与 Deno 开发，你可能想要自己从源码编译 Deno 。

运行以下命令会以调试用设置编译 Deno 。

```bash
# Fetch deps.
git clone --recurse-submodules https://github.com/denoland/deno.git
cd deno
# Setup and download important third party tools
./tools/setup.py
# Build.
./tools/build.py
```

{% hint style="info" %}
在某些国家，google.com 之类的域名受到限制无法访问。你可能需要通过 VPN 或类似工具运行 `./tools/setup.py` 。
{% endhint %}

Deno 的编译使用 GN 和 Ninja ，它们也是 Chromium 团队的编译工具。编译结果会放在 `target/debug/` 。

另外，要以发布用设置编译试用的话，请将 DENO\_BUILD\_MODE 设为 release 再编译:

```bash
DENO_BUILD_MODE=release ./tools/build.py
```

编译结果会放在 `target/release/` 。

Deno 也支持使用 Cargo 编译：

```bash
cargo build
```

