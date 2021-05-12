
# Troubleshooting

This page contains listings of commonplace (and less commonplace) issues related to the Flax Editor and Engine, and their respective possible solutions.


## Intel iGPUs and DirectX Error `E_INVALIDARG`


### Symptoms:
When attempting to build scene data, Flax Editor crashes and displays an error message:

![Crash Error Message](https://i.imgur.com/40WoTUy.png)


### Causes:
This is caused by a broken Shader Model 5 implementation in certain Intel Chipsets, related to Direct X 11.\
Simply put, the Intel graphics lies about supporting certain DirectX 11 features, and then throws an error when anything tries using the features it pretendes to support. This in turn crashes any application or game that doesn't specifically distrust Intel iGPUs.


### Solutions & Workarounds:
It is possible to work around the issue by forcing Flax Editor to run in DirectX 10 mode using [command line parameters](https://docs.flaxengine.com/manual/editor/advanced/command-line-access.html).\
This forces Flax Editor to use Shader Model 4 and thus bypasses the Intel SM5 issue entirely.


To do this, create a BAT file or a shortcut to FlaxEditor.exe using the following parameters:

`FlaxEditor.exe -project "C:\Users\<Username>\Documents\Flax Projects\YourProject" -d3d10`

> **Note:**\
> *Please keep in mind that the DirectX 10 backend isn't optimized,\
> and might occasionally not support a given feature.*
