# dji_tello_ws
Main Workspace for drone tello for FlyingRobots


para configurar esse repositorio, use o ros2 humble

1. clone de forma recursiva o repositorio

```bash
git clone https://github.com/MarceloJordao01/dji_tello_ws.git --recursive
```

2. Faça o install das dependencias
```bash
sudo apt update
sudo apt install -y gazebo11 libgazebo11 libgazebo11-dev ros-humble-gazebo-ros ros-humble-gazebo-plugins ros-humble-gazebo-msgs libasio-dev ros-humble-cv-bridge ros-humble-camera-calibration-parsers
python3 -m pip install --user transformations
```

3. Ainda precisa fazer isso dentro do ws

```bash
chmod +x /src/tello_ros/tello_description/src/replace.py
```

Para rodar a simulação
1. Exporte o caminho do modelo do tello (rode o comando dentro do ws)

```bash
export GAZEBO_MODEL_PATH=${PWD}/install/tello_gazebo/share/tello_gazebo/models/:$GAZEBO_MODEL_PATH
```

2. Depois inicie a simulação

```bash
ros2 launch tello_gazebo simple_launch.py
```

3. Use os serviços para fazer o tello voar, como o de takeoff

```bash
ros2 service call /drone1/tello_action tello_msgs/TelloAction "{cmd: 'takeoff'}"
```