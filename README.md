# Создание квартиры с помощью Gazebo, Ignition Gazebo и TurtleBot4

## Создание 2D модели квартиры
1. Открываем Gazebo и выбираем "Edit/Building Editor".
   
`gazebo`

2. Рисуем план квартиры. Устанавливаем двери и окна, с помошью интрументов Wall, Door, Window.
![](https://github.com/aryunae/Ros-2-TurtleBot4-Flat/blob/main/%D1%80%D0%B8%D1%811.jpg)
![](https://github.com/aryunae/Ros-2-TurtleBot4-Flat/blob/main/%D1%80%D0%B8%D1%812.jpg)
4. Сохраняем модель (получаем 2 файла - model.sdf и model.config в папке building_editor_models)


## Gazebo Ignition
1. Создаем файл world.sdf в папке building_editor_models

```
<?xml version="1.0" ?>
<sdf version="1.6">
  <world name="default">
    <include>
     <uri>file:///home/aryuna/building_editor_models/Untitled/model.sdf</uri>
    </include>
  </world>
</sdf>
```


```
export
GZ_SIM_RESOURCE_PATH="/home/aryuna/building_editor_models/Untitled"
```
3. Открываем мир с помощью команды
`ign gazebo world.sdf`
4. Нажимаем на "Resourse Spawner"
5. Выбираем в поиске ground_plane(земля) и sun(свет). Далее выбираем мебель.
6. Сохраняем мир через "Save world as", файл с раширением sdf (world.sdf), ставим галочки "Expand include tags" и "Save Fuel model version".
![](https://github.com/aryunae/Ros-2-TurtleBot4-Flat/blob/main/%D1%80%D0%B8%D1%813.jpg)

## TurtleBot4
1. Создаем рабочее пространство
```
mkdir -p ~/turtlebot4_ws/src
cd ~/turtlebot4_ws/src
git clone https://github.com/turtlebot/turtlebot4.git
cd ~/turtlebot4_ws
colcon build --symlink-install
```
2. Запускаем
```
ros2 launch turtlebot4_ignition_bringup turtlebot4_ignition.launch.py nav2:=true slam:=false localization:=true rviz:=true
```
 
