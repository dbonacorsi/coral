## Getting started

Download and unpack the Edge TPU runtime:

```
curl -O https://dl.google.com/coral/edgetpu_api/edgetpu_runtime_20200728.zip
unzip edgetpu_runtime_20200728.zip
```

Install the Edge TPU runtime:

```
cd edgetpu_runtime
sudo bash install.sh
```

The installation script will ask whether you want to enable the maximum operating frequency. Running at the maximum operating frequency increases the inferencing speed but also increases power consumption and causes the USB Accelerator to become very hot. If you're not certain your application requires increased performance, you should type "N" to use the reduced operating frequency.

You can read more about the performance setting in the USB Accelerator datasheet (https://coral.ai/docs/accelerator/datasheet/#performance-settings).

Now connect the USB Accelerator to your computer using the provided USB 3.0 cable.

Then continue to install the TensorFlow Lite library (https://coral.ai/docs/accelerator/get-started/#2-install-the-tensorflow-lite-library)

Python quickstart
Using TensorFlow Lite with Python is great for embedded devices based on Linux, such as Raspberry Pi and Coral devices with Edge TPU, among many others.

This page shows how you can start running TensorFlow Lite models with Python in just a few minutes. All you need is a TensorFlow model converted to TensorFlow Lite. (If you don't have a model converted yet, you can experiment using the model provided with the example linked below.)

Install just the TensorFlow Lite interpreter
To quickly run TensorFlow Lite models with Python, you can install just the TensorFlow Lite interpreter, instead of all TensorFlow packages.

This interpreter-only package is a fraction the size of the full TensorFlow package and includes the bare minimum code required to run inferences with TensorFlow Lite—it includes only the tf.lite.Interpreter Python class. This small package is ideal when all you want to do is execute .tflite models and avoid wasting disk space with the large TensorFlow library.

Note: If you need access to other Python APIs, such as the TensorFlow Lite Converter, you must install the full TensorFlow package.
To install, run pip3 install and pass it the appropriate Python wheel URL from the following table.

For example, if you have a Raspberry Pi that's running Raspberry Pi OS 10 (which has Python 3.7), install the Python wheel as follows:

NO

for Mojave, take list here 

https://www.tensorflow.org/lite/guide/python

macOS 10.14 	3.5 	https://dl.google.com/coral/python/tflite_runtime-2.1.0.post1-cp35-cp35m-macosx_10_14_x86_64.whl
3.6 	https://dl.google.com/coral/python/tflite_runtime-2.1.0.post1-cp36-cp36m-macosx_10_14_x86_64.whl
3.7 	https://dl.google.com/coral/python/tflite_runtime-2.1.0.post1-cp37-cp37m-macosx_10_14_x86_64.whl

(base) Daniele-Bonacorsis-MacBook-Pro-6218:~ bonacor$ mkdir CORAL
(base) Daniele-Bonacorsis-MacBook-Pro-6218:~ bonacor$ cd CORAL
(base) Daniele-Bonacorsis-MacBook-Pro-6218:CORAL bonacor$ curl -O https://dl.google.com/coral/edgetpu_api/edgetpu_runtime_20200728.zip
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 16.0M  100 16.0M    0     0   766k      0  0:00:21  0:00:21 --:--:-- 1103k
(base) Daniele-Bonacorsis-MacBook-Pro-6218:CORAL bonacor$ ls
edgetpu_runtime_20200728.zip
(base) Daniele-Bonacorsis-MacBook-Pro-6218:CORAL bonacor$ unzip edgetpu_runtime_20200728.zip
Archive:  edgetpu_runtime_20200728.zip
   creating: edgetpu_runtime/
  inflating: edgetpu_runtime/uninstall.bat
   creating: edgetpu_runtime/libedgetpu/
  inflating: edgetpu_runtime/libedgetpu/edgetpu.h
  inflating: edgetpu_runtime/libedgetpu/edgetpu-accelerator.rules
   creating: edgetpu_runtime/libedgetpu/throttled/
   creating: edgetpu_runtime/libedgetpu/throttled/x64_windows/
  inflating: edgetpu_runtime/libedgetpu/throttled/x64_windows/edgetpu.dll
  inflating: edgetpu_runtime/libedgetpu/throttled/x64_windows/edgetpu.dll.if.lib
   creating: edgetpu_runtime/libedgetpu/throttled/aarch64/
  inflating: edgetpu_runtime/libedgetpu/throttled/aarch64/libedgetpu.so.1.0
  inflating: edgetpu_runtime/libedgetpu/throttled/aarch64/libedgetpu.so.1
   creating: edgetpu_runtime/libedgetpu/throttled/armv6/
  inflating: edgetpu_runtime/libedgetpu/throttled/armv6/libedgetpu.so.1.0
  inflating: edgetpu_runtime/libedgetpu/throttled/armv6/libedgetpu.so.1
   creating: edgetpu_runtime/libedgetpu/throttled/k8/
  inflating: edgetpu_runtime/libedgetpu/throttled/k8/libedgetpu.so.1.0
  inflating: edgetpu_runtime/libedgetpu/throttled/k8/libedgetpu.so.1
   creating: edgetpu_runtime/libedgetpu/throttled/darwin/
  inflating: edgetpu_runtime/libedgetpu/throttled/darwin/libedgetpu.1.dylib
  inflating: edgetpu_runtime/libedgetpu/throttled/darwin/libedgetpu.1.0.dylib
   creating: edgetpu_runtime/libedgetpu/throttled/armv7a/
  inflating: edgetpu_runtime/libedgetpu/throttled/armv7a/libedgetpu.so.1.0
  inflating: edgetpu_runtime/libedgetpu/throttled/armv7a/libedgetpu.so.1
  inflating: edgetpu_runtime/libedgetpu/LICENSE.txt
   creating: edgetpu_runtime/libedgetpu/direct/
   creating: edgetpu_runtime/libedgetpu/direct/x64_windows/
  inflating: edgetpu_runtime/libedgetpu/direct/x64_windows/edgetpu.dll
  inflating: edgetpu_runtime/libedgetpu/direct/x64_windows/edgetpu.dll.if.lib
   creating: edgetpu_runtime/libedgetpu/direct/aarch64/
  inflating: edgetpu_runtime/libedgetpu/direct/aarch64/libedgetpu.so.1.0
  inflating: edgetpu_runtime/libedgetpu/direct/aarch64/libedgetpu.so.1
   creating: edgetpu_runtime/libedgetpu/direct/armv6/
  inflating: edgetpu_runtime/libedgetpu/direct/armv6/libedgetpu.so.1.0
  inflating: edgetpu_runtime/libedgetpu/direct/armv6/libedgetpu.so.1
   creating: edgetpu_runtime/libedgetpu/direct/k8/
  inflating: edgetpu_runtime/libedgetpu/direct/k8/libedgetpu.so.1.0
  inflating: edgetpu_runtime/libedgetpu/direct/k8/libedgetpu.so.1
   creating: edgetpu_runtime/libedgetpu/direct/darwin/
  inflating: edgetpu_runtime/libedgetpu/direct/darwin/libedgetpu.1.dylib
  inflating: edgetpu_runtime/libedgetpu/direct/darwin/libedgetpu.1.0.dylib
   creating: edgetpu_runtime/libedgetpu/direct/armv7a/
  inflating: edgetpu_runtime/libedgetpu/direct/armv7a/libedgetpu.so.1.0
  inflating: edgetpu_runtime/libedgetpu/direct/armv7a/libedgetpu.so.1
  inflating: edgetpu_runtime/libedgetpu/BUILD
  inflating: edgetpu_runtime/libedgetpu/edgetpu_c.h
  inflating: edgetpu_runtime/install.bat
  inflating: edgetpu_runtime/uninstall.sh
   creating: edgetpu_runtime/third_party/
   creating: edgetpu_runtime/third_party/libusb_win/
  inflating: edgetpu_runtime/third_party/libusb_win/libusb-1.0.dll
  inflating: edgetpu_runtime/third_party/libusb_win/README
   creating: edgetpu_runtime/third_party/usbdk/
  inflating: edgetpu_runtime/third_party/usbdk/UsbDk_1.0.21_x64.msi
  inflating: edgetpu_runtime/third_party/usbdk/LICENSE
   creating: edgetpu_runtime/third_party/coral_accelerator_windows/
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/coral.man
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/coral.sys
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/Coral_USB_Accelerator.inf
   creating: edgetpu_runtime/third_party/coral_accelerator_windows/amd64/
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/amd64/WdfCoInstaller01009.dll
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/amd64/winusbcoinstaller2.dll
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/amd64/license.rtf
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/coral.cat
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/Coral_USB_Accelerator_(DFU).inf
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/Coral_USB_Accelerator.cat
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/Coral_USB_Accelerator_(DFU).cat
  inflating: edgetpu_runtime/third_party/coral_accelerator_windows/coral.inf
  inflating: edgetpu_runtime/install.sh
(base) Daniele-Bonacorsis-MacBook-Pro-6218:CORAL bonacor$ cd edgetpu_runtime
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$ ls
install.bat	install.sh	libedgetpu	third_party	uninstall.bat	uninstall.sh
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$ sudo bash install.sh
Password:
Warning: If you're using the Coral USB Accelerator, it may heat up during operation, depending
on the computation workloads and operating frequency. Touching the metal part of the USB
Accelerator after it has been operating for an extended period of time may lead to discomfort
and/or skin burns. As such, if you enable the Edge TPU runtime using the maximum operating
frequency, the USB Accelerator should be operated at an ambient temperature of 25°C or less.
Alternatively, if you enable the Edge TPU runtime using the reduced operating frequency, then
the device is intended to safely operate at an ambient temperature of 35°C or less.

Google does not accept any responsibility for any loss or damage if the device
is operated outside of the recommended ambient temperature range.

Note: This question affects only USB-based Coral devices, and is irrelevant for PCIe devices.
................................................................................
Would you like to enable the maximum operating frequency for your Coral USB device? Y/N
Y
Using the maximum operating frequency for Coral USB devices.
Updating Homebrew...
==> Downloading https://homebrew.bintray.com/bottles-portable-ruby/portable-ruby-2.6.3_2.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring portable-ruby-2.6.3_2.yosemite.bottle.tar.gz
==> Auto-updated Homebrew!
Updated 1 tap (homebrew/core).
==> New Formulae
acl2                           fetch                          libhandy                       protoc-gen-go-grpc
act                            flamegraph                     libice                         protoc-gen-gogo
airshare                       flank                          libirecovery                   protoc-gen-gogofaster
alsa-lib                       flarectl                       libmnl                         publish
amp                            flash                          libnetfilter-queue             pwncat
apidoc                         fleet-cli                      libnetworkit                   python@3.7
arb                            flit                           libnfnetlink                   python@3.9
archiver                       folderify                      libolm                         qp
argo                           font-util                      liboqs                         qrcp
argocd                         forcecli                       libpciaccess                   quill
arrayfire                      foreman                        libpqxx@6                      rain
arturo                         fpart                          libpthread-stubs               rbtools
asimov                         fpdns                          libseccomp                     rcm
asroute                        fplll                          libsm                          redo
asuka                          functionalplus                 libtorrent-rakshasa            reg
athenacli                      gateway-go                     libx11                         reorder-python-imports
austin                         gau                            libxau                         rgf
autodiff                       gcalcli                        libxaw                         rqlite
awsweeper                      gcc@9                          libxaw3d                       rtorrent
azcopy                         gdbgui                         libxcb                         rust-analyzer
bcoin                          geph2                          libxcomposite                  rustscan
beancount                      ghc@8.8                        libxcursor                     s2n
blaze                          ghz                            libxdamage                     saltwater
blogc                          ghz-web                        libxdmcp                       scw@1
bnfc                           git-bug                        libxext                        sdns
bombadillo                     git-hooks-go                   libxfixes                      semgrep
bond                           git-hound                      libxfont                       semtag
bootloadhid                    git-remote-codecommit          libxft                         server-go
borgbackup                     git-trim                       libxi                          shallow-backup
box2d                          gitlint                        libxinerama                    sheldon
buildozer                      gitql                          libxkbfile                     shtools
c7n                            gitui                          libxmu                         silicon
cadence                        gluon                          libxpm                         simdjson
carton                         gmailctl                       libxrandr                      skylighting
cassowary                      go-jsonnet                     libxrender                     sleef
castget                        go@1.14                        libxres                        smlpkg
cbc                            gobo                           libxscrnsaver                  snap
cbmc                           gocloc                         libxshmfence                   so
ccheck                         gofish                         libxt                          solidity
cddlib                         golangci-lint                  libxtst                        sollya
cdk8s                          googletest                     libxv                          sonic
cdktf                          gost                           libxvmc                        sponge
cdo                            gostatic                       libxxf86dga                    spotify-tui
cgl                            gradle-profiler                libxxf86vm                     spotifyd
chalk-cli                      graphql-cli                    litecli                        sqlite-utils
charge                         gravity                        lizard-analyzer                standardese
chart-testing                  grpcui                         llvm@9                         staticcheck
chezmoi                        guile@2                        localstack                     structurizr-cli
choose-rust                    gulp-cli                       logcli                         subfinder
chrony                         halide                         loki                           swift-format
clair                          hashlink                       lunchy                         tanka
clang-format@8                 hasura-cli                     lunchy-go                      taskwarrior-tui
claws-mail                     hcxtools                       macos-trash                    tengo
cli11                          hdf5-mpi                       mandown                        termcolor
clip                           hdf5@1.10                      mariadb@10.4                   terraform-ls
cloud-nuke                     hdt                            marked                         terraform@0.12
cloudformation-cli             heksa                          mask                           terrascan
cloudformation-guard           hsd                            matplotplusplus                tfsec
coconut                        httpx                          mhonarc                        thanos
code-server                    hy                             microplane                     tlx
colfer                         i686-elf-binutils              minipro                        toot
commitizen                     i686-elf-gcc                   mockolo                        torchvision
confd                          idris2                         mtoc                           trailscraper
container-structure-test       immudb                         naabu                          tre-command
copilot                        infracost                      nanorc                         trimage
coredns                        inja                           nef                            trunk
cortex                         inko                           nest                           ugrep
cpio                           inxi                           networkit                      unum
cpm                            ioctl                          never                          uptoc
cpr                            isort                          newrelic-cli                   usb.ids
cqlkit                         jc                             nfpm                           util-macros
croaring                       jerryscript                    ngs                            uutils-coreutils
croc                           jimtcl                         nicotine-plus                  vapor
cubejs-cli                     jinx                           notmuch-mutt                   vcpkg
cucumber-ruby                  jobber                         numcpp                         vgrep
cvs-fast-export                jolie                          oci-cli                        vint
datasette                      jsonnet-bundler                odin                           vivid
dbdeployer                     k9s                            oha                            vlang
detach                         kamel                          oil                            vlmcsd
device-mapper                  kde-extra-cmake-modules        omake                          volk
dgraph                         kde-karchive                   openfast                       volta
dhall-yaml                     kde-kdoctools                  openfst                        vpn-slice
diskonaut                      kde-ki18n                      openjdk@8                      vroom
dmagnetic                      kde-threadweaver               openstackclient                vsearch
dnsprobe                       kona                           oq                             vtk@8.2
doctest                        kondo                          or-tools                       wasm-pack
dolt                           ksync                          ormolu                         webify
dosbox-staging                 kubie                          ory-hydra                      wgcf
dotnet                         kumactl                        osi                            wolfmqtt
duckdb                         ladspa-sdk                     osm                            wownero
duckscript                     lanraragi                      packetbeat                     wren
duktape                        latexindent                    packr                          wren-cli
earthly                        lc0                            pandoc-include-code            x86_64-elf-gdb
eksctl                         ldpl                           pandocomatic                   xcb-proto
eleventy                       leaf                           parallel-hashmap               xclogparser
emacs-dracula                  leakcanary-shark               pass-git-helper                xdpyinfo
empty                          libaio                         periscope                      xorgproto
envoy                          libcouchbase@2                 pfetch                         xtrans
erlang@22                      libcpuid                       pickle                         xxh
eva                            libdmx                         pipgrip                        yj
fargatecli                     libdrm                         po4a                           z.lua
fava                           libfontenc                     podman                         zenith
fblog                          libfs                          postgresql@12                  zoxide
fcct                           libgccjit                      prometheus-cpp                 zsh-you-should-use
fennel                         libgnt                         promtail
==> Updated Formulae
Updated 4598 formulae.
==> Renamed Formulae
elasticsearch@6.8 -> elasticsearch@6                          jfrog-cli-go -> jfrog-cli
gst-validate -> gst-devtools                                  kibana@6.8 -> kibana@6
interactive-rebase-tool -> git-interactive-rebase-tool        mkl-dnn -> onednn
==> Deleted Formulae
python ✔            ck                  djmount             i386-elf-grub       open-cobol          unravel
apache-zeppelin     compcert            elasticsearch@2.4   kibana@5.6          pijul               urbit
baidupcs-go         crc                 elasticsearch@5.6   llvm@6              residualvm          woboq_codebrowser
biogeme             cryptopp            gmediaserver        lumo                sflowtool           wpscan
camlp4              deis                gnome-builder       marathon-swift      syncthing-inotify   xu4
cargo-completion    deisctl             highlighting-kate   meson-internal      tomee-jax-rs

Warning: libusb 1.0.23 is already installed and up-to-date
To reinstall 1.0.23, run `brew reinstall libusb`
Installing Edge TPU runtime library [/usr/local/lib]...
Installing Edge TPU runtime library symlink [/usr/local/lib]...
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$ pip3 install https://dl.google.com/coral/python/tflite_runtime-2.1.0.post1-cp37-cp37m-macosx_10_14_x86_64.whl
Collecting tflite-runtime==2.1.0.post1
  Downloading https://dl.google.com/coral/python/tflite_runtime-2.1.0.post1-cp37-cp37m-macosx_10_14_x86_64.whl (1.2MB)
     |████████████████████████████████| 1.2MB 342kB/s
Requirement already satisfied: numpy>=1.12.1 in /usr/local/lib/python3.7/site-packages (from tflite-runtime==2.1.0.post1) (1.18.1)
Installing collected packages: tflite-runtime
Successfully installed tflite-runtime-2.1.0.post1
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$ pwd
/Users/bonacor/CORAL/edgetpu_runtime
(base) Daniele-Bonacorsis-MacBook-Pro-6218:edgetpu_runtime bonacor$ cd ..
(base) Daniele-Bonacorsis-MacBook-Pro-6218:CORAL bonacor$ mkdir coral
(base) Daniele-Bonacorsis-MacBook-Pro-6218:CORAL bonacor$ cd coral
(base) Daniele-Bonacorsis-MacBook-Pro-6218:coral bonacor$ git clone https://github.com/google-coral/tflite.git
Cloning into 'tflite'...
remote: Enumerating objects: 65, done.
remote: Counting objects: 100% (65/65), done.
remote: Compressing objects: 100% (34/34), done.
remote: Total 193 (delta 23), reused 59 (delta 19), pack-reused 128
Receiving objects: 100% (193/193), 675.90 KiB | 1.36 MiB/s, done.
Resolving deltas: 100% (69/69), done.
(base) Daniele-Bonacorsis-MacBook-Pro-6218:coral bonacor$ cd tflite/python/examples/classification
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$ bash install_requirements.sh
Requirement already satisfied: numpy in /usr/local/lib/python3.7/site-packages (1.18.1)
Collecting Pillow
  Downloading https://files.pythonhosted.org/packages/30/aa/4254943b3e9caedd1736b0158a242d4f733f14f75203862ee828a033648c/Pillow-8.0.1-cp37-cp37m-macosx_10_10_x86_64.whl (2.2MB)
     |████████████████████████████████| 2.2MB 1.9MB/s
Installing collected packages: Pillow
Successfully installed Pillow-8.0.1
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   189  100   189    0     0    329      0 --:--:-- --:--:-- --:--:--   329
100 3972k  100 3972k    0     0  1339k      0  0:00:02  0:00:02 --:--:-- 1834k
100   181  100   181    0     0    451      0 --:--:-- --:--:-- --:--:--   451
100 3448k  100 3448k    0     0  1114k      0  0:00:03  0:00:03 --:--:-- 2040k
100   158  100   158    0     0    835      0 --:--:-- --:--:-- --:--:--   835
100 40895  100 40895    0     0    97k      0 --:--:-- --:--:-- --:--:--   97k
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   148  100   148    0     0    517      0 --:--:-- --:--:-- --:--:--   515
100  582k  100  582k    0     0   444k      0  0:00:01  0:00:01 --:--:-- 2197k
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$ python3 classify_image.py \
> --model models/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite \
> --labels models/inat_bird_labels.txt \
> --input images/parrot.jpg
Traceback (most recent call last):
  File "/usr/local/lib/python3.7/site-packages/tflite_runtime/interpreter.py", line 161, in load_delegate
    delegate = Delegate(library, options)
  File "/usr/local/lib/python3.7/site-packages/tflite_runtime/interpreter.py", line 120, in __init__
    raise ValueError(capture.message)
ValueError

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "classify_image.py", line 122, in <module>
    main()
  File "classify_image.py", line 99, in main
    interpreter = make_interpreter(args.model)
  File "classify_image.py", line 73, in make_interpreter
    {'device': device[0]} if device else {})
  File "/usr/local/lib/python3.7/site-packages/tflite_runtime/interpreter.py", line 164, in load_delegate
    library, str(e)))
ValueError: Failed to load delegate from libedgetpu.1.dylib

(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$ ls
README.md		classify.py		images			models
__pycache__		classify_image.py	install_requirements.sh
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$ python3 classify_image.py --model models/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite --labels models/inat_bird_labels.txt --input images/parrot.jpg
Traceback (most recent call last):
  File "/usr/local/lib/python3.7/site-packages/tflite_runtime/interpreter.py", line 161, in load_delegate
    delegate = Delegate(library, options)
  File "/usr/local/lib/python3.7/site-packages/tflite_runtime/interpreter.py", line 120, in __init__
    raise ValueError(capture.message)
ValueError

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "classify_image.py", line 122, in <module>
    main()
  File "classify_image.py", line 99, in main
    interpreter = make_interpreter(args.model)
  File "classify_image.py", line 73, in make_interpreter
    {'device': device[0]} if device else {})
  File "/usr/local/lib/python3.7/site-packages/tflite_runtime/interpreter.py", line 164, in load_delegate
    library, str(e)))
ValueError: Failed to load delegate from libedgetpu.1.dylib

(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$ python3 classify_image.py --model models/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite --labels models/inat_bird_labels.txt --input images/parrot.jpg
----INFERENCE TIME----
Note: The first inference on Edge TPU is slow because it includes loading the model into Edge TPU memory.
14.8ms
3.4ms
3.3ms
3.2ms
3.4ms
-------RESULTS--------
Ara macao (Scarlet Macaw): 0.77734
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$ python3 classify_image.py --model models/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite --labels models/inat_bird_labels.txt --input images/parrot.jpg
----INFERENCE TIME----
Note: The first inference on Edge TPU is slow because it includes loading the model into Edge TPU memory.
12.7ms
2.6ms
2.7ms
2.8ms
3.0ms
-------RESULTS--------
Ara macao (Scarlet Macaw): 0.77734
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$ python3 classify_image.py --model models/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite --labels models/inat_bird_labels.txt --input images/parrot.jpg
----INFERENCE TIME----
Note: The first inference on Edge TPU is slow because it includes loading the model into Edge TPU memory.
14.9ms
3.3ms
3.4ms
3.1ms
3.2ms
-------RESULTS--------
Ara macao (Scarlet Macaw): 0.77734
(base) Daniele-Bonacorsis-MacBook-Pro-6218:classification bonacor$ python3 classify_image.py --model models/mobilenet_v2_1.0_224_inat_bird_quant_edgetpu.tflite --labels models/inat_bird_labels.txt --input images/parrot.jpg
----INFERENCE TIME----
Note: The first inference on Edge TPU is slow because it includes loading the model into Edge TPU memory.
14.2ms
3.1ms
3.0ms
3.1ms
3.3ms
-------RESULTS--------
Ara macao (Scarlet Macaw): 0.77734

