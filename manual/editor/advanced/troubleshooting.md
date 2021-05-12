
# Troubleshooting

This page contains listings of commonplace (and less commonplace) issues related to the Flax Editor and Engine, and their respective possible solutions.


## Intel iGPUs and DirectX Error `E_INVALIDARG`


### Symptoms:
When attempting to build scene data, the Flax Editor crashes and displays an error message:

![Crash Error Message](https://i.imgur.com/L1JnGYb.png)


### Causes:
This is caused by a broken SM5 shader implementation in certain Intel Chipsets.\
Essentially, the Intel graphics lies about supporting certain functionality, and then errors when DirectX calls those functions it lied about supporting. Thanks ~~Obama~~ *Intel*.


### Solutions & Workarounds
It is possible to bypass the issue by forcing Flax Editor to run in DirectX 10 mode using [command line parameters](https://docs.flaxengine.com/manual/editor/advanced/command-line-access.html). This forces Flax to use SM4 and DirextX 10 compatibility, 

Creating a BAT file or a shortcut to FlaxEditor.exe using the following parameters will force DX10:

`FlaxEditor.exe -project "C:\Users\<Username>\Documents\Flax Projects\YourProject" -d3d10`

> **Note:**\
> *Please keep in mind that the DirectX 10 backend isn't optimized,\
> and might occasionally not support a given feature.*
