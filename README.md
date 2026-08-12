# MaxiGen
MaxiGen is a thirdparty framegeneration program for linux.


1. Global Installation (Required for Both Steam & Lutris)

Before configuring your game launchers, the layer files must be placed in your system's user Vulkan layer directory so the system can recognize them.

    Open your terminal or file manager and navigate to:
    ~/.local/share/vulkan/implicit_layer.d/
    (Create the folders vulkan and implicit_layer.d inside ~/.local/share/ if they do not exist).

    Place these two files inside that directory:

        libMaxiGen.so

        VkLayer_MaxiGen.json

    Warning: Do not place these files inside individual game installation folders, especially for games with anti-cheat software, as it can cause crashes or game bans. MaxiGen requires a game that natively supports the Vulkan API.

2. Configuration for Steam

If you want to use MaxiGen with a game running through Steam (Proton/Linux native Vulkan games):

    Open Steam and go to your Library.

    Right-click the game you want to play and select Properties.

    Under the General tab, find the Launch Options text box.

    Paste the following command into the box:
    Bash

    ENABLE_VK_LAYER_MAXIGEN_frame_gen=1 VK_INSTANCE_LAYERS=VK_LAYER_MaxiGen %command%

    Close the window and launch the game.

3. Configuration for Lutris

If you want to force-enable the layer for a specific game running through Lutris:

    Open Lutris, right-click your game, and select Configure.

    Switch to the System options tab (make sure Advanced mode is toggled on at the top of Lutris if you don't see all options).

    Scroll down to the Environment variables section and click the Add button.

    Add these two variables one by one:

        Variable 1:

            Key: ENABLE_VK_LAYER_MAXIGEN_frame_gen

            Value: 1

        Variable 2:

            Key: VK_INSTANCE_LAYERS

            Value: VK_LAYER_MaxiGen

    Click Save.

4. Verifying via Terminal

To check if the layer is initializing properly:

    Close Lutris or Steam if they are running in the background.

    Open your terminal and launch Lutris with debugging enabled:
    Bash

    lutris -d

    Start your game and look at the terminal logs to verify that MaxiGen initializes successfully.
