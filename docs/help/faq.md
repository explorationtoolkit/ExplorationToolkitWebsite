icon: material/chat-question-outline

# :material-chat-question-outline: FAQ

## Importing

??? question "Why am I getting errors after importing."

    This might be due to your project lacking certain Unity packages. Make sure your project has the following installed:

    * com.unity.inputsystem
    * com.unity.ugui

??? question "Why is my UI text invisible after importing?"

    The toolkit uses TextMeshPro, so make sure to install the essentials. A popup should appear to do so after importing the toolkit.

## Editor

??? question "I changed a variable in a script. Now when I view that component in the Inspector, I get a NullReferenceException error."

    Many of the toolkit's components have custom editors. If you ever want to change the name of a variable, or add/remove one, you will also need to update its corresponding inspector script, located in the `Core > Editor > Custom Inspectors` folder. Learn about how custom inspectors are used in the toolkit [here](../scripting/custom-inspectors.md).

## Systems

??? question "How can I use my own player controller?"

    Refer to the documentation [here](../player/custom-player-controller.md) on implementing a custom player controller.

??? question "The inspect screen is not appearing when I inspect an object."

    Make sure you are adding the InspectCamera to your main camera's stack. This is an overlay camera, and it must be added to the camera stack to work.