## Building just the `ipa_room_segmentation` package.

1. Clone this repository in a catkin workspace
    ```
    cd ~/catkin_ws/src
    git clone git@github.com:Sushant-Chavan/autopnp.git
    ```

2. Disable building undesired packages
    ```
    touch src/autopnp/autopnp/CATKIN_IGNORE
    touch src/autopnp/autopnp_dirt_detection/CATKIN_IGNORE
    touch src/autopnp/autopnp_moveit_config/CATKIN_IGNORE
    touch src/autopnp/autopnp_tool_change/CATKIN_IGNORE
    touch src/autopnp/ipa_room_exploration/CATKIN_IGNORE
    touch src/autopnp/autopnp_can_attachments/CATKIN_IGNORE
    touch src/autopnp/autopnp_gui/CATKIN_IGNORE
    touch src/autopnp/autopnp_scenario/CATKIN_IGNORE
    touch src/autopnp/cob_laser_scanner_filter/CATKIN_IGNORE
    touch src/autopnp/ipa_building_navigation/CATKIN_IGNORE
    touch src/autopnp/xme/CATKIN_IGNORE
    ```

3. Build the `ipa_room_segmentation` package.
    ```
    catkin build ipa_room_segmentation
    ```

## Building all the packages in the repository

1. Create a directory for all the related packages and fetch the packages
    ```
    mkdir -p ~/catkin_ws/src/ipa_packages
    cd ~/catkin_ws
    wstool init src/ipa_packages
    wstool merge -t src/ipa_packages https://raw.githubusercontent.com/Sushant-Chavan/autopnp/kinetic/.rosinstall
    wstool update -t src/ipa_packages
    rosdep install --from-paths src/ipa_packages --ignore-src --rosdistro=kinetic -y
    ```
2. Ignore building some packages that are currently failing to build
    ```
    touch src/ipa_packages/cob_object_perception/cob_object_categorization/CATKIN_IGNORE 
    touch src/ipa_packages/autopnp/autopnp_tool_change/CATKIN_IGNORE
    touch src/ipa_packages/autopnp/autopnp_scenario/CATKIN_IGNORE
    touch src/ipa_packages/autopnp/xme/CATKIN_IGNORE
    touch src/ipa_packages/autopnp/autopnp_dirt_detection/CATKIN_IGNORE
    ```

3. Build the code
    ```
    catkin build
    ```
