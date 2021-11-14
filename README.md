# ROS 2演習

Windows 10 WSL2（Ubuntu 20.04）での演習を想定しています。

## ROS 2の構築

- ROSを利用したことある場合 (利用したことがない場合は不要)

ROSを利用したことがない人は「[APTリポジトリの追加](#aptリポジトリの追加)」（次の項目） から進めてください。

.bashrcの以下などROSの設定箇所をコメントアウト
```text
#source /opt/ros/noetic/setup.bash
#source ~/catkin_ws/devel/setup.bash
```
変更した設定を反映
```shell
source ~/.bashrc
```

- APTリポジトリの追加・更新

```shell
sudo apt update && sudo apt install curl gnupg2 lsb-release
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key  -o /usr/share/keyrings/ros-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
sudo apt update
```

- ROS 2のインストール (ROS 2 Version Foxy)

```shell
sudo apt install ros-foxy-desktop
```

- 環境設定
```shell
echo "source /opt/ros/foxy/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

- colcon build インストール
```shell
sudo apt install python3-colcon-common-extensions
```

- ROS2 コマンド自動補完のインストール
```shell
sudo apt install python3-argcomplete
```

## 環境設定

- colconの設定
```shell
echo "source /usr/share/colcon_cd/function/colcon_cd.sh" >> ~/.bashrc
echo "export _colcon_cd_root=~/ros2_install" >> ~/.bashrc
```

- 環境の確認
```shell
 printenv | grep -i ROS_
```

出力例
```
ROS_VERSION=2  
ROS_PYTHON_VERSION=3 
ROS_LOCALHOST_ONLY=0 
ROS_DISTRO=foxy 
```

- domain_idの設定

> export ROS_DOMAIN_ID=<your_domain_id>

your_domain_idは0～65532で選択

your_domain_idが１の場合の例
```
echo "export ROS_DOMAIN_ID=1">> ~/.bashrc
```

変更した設定を反映
```shell
source ~/.bashrc
```

