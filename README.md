# side by side installation of visual studio for windows

Whilst Microsoft offers older versions of Visual Studio for download [via my.visualstudio.com](https://t.co/HJgKTpg5mq?amp=1), Microsoft do not offer a way to install a specific patch release. Having the latest of a minor is generally not enough, as new revisions/patch releases can break behaviors. Personally, I've lost _days_ to _weeks_ levels of productivity this year with Visual Studio for Windows after upgrading and then being stuck unable to re-install a specific, known working version.

This community maintained repository allows you to install a specific `productSemanticVersion` of Visual Studio. 

## usage

- Cherry pick a particular version and place in `C:\ProgramData\Microsoft\VisualStudio\Packages\_Instances` or as an administrator, after uninstalling all editions of visual studio for windows, clone this repository as `C:\ProgramData\Microsoft\VisualStudio\Packages\_Instances`

```bash
cd C:\ProgramData\Microsoft\VisualStudio\Packages
git clone https://github.com/ghuntley/visual-studio-for-windows-layouts _Instances
```

- **Optional:** Open the `state.json` file and adjust the `installationPath` to different drive or folder.
- Launch the Visual Studio Installer.
- On the layout you wish to install, click retry and then click finish.

## contributing

1. Format the `state.json` with a JSON pretty printer.
2. Adjust `"installationPath":` to follow the convention `"C:\\VisualStudio\\{Edition}\\{catalogInfo.productSemanticVersion}"` ie. `C:\\VisualStudio\\Enterprise\\15.9.14+28307.770`
3. Adjust `"properties.nickname:"` to be `"{catalogInfo.productSemanticVersion}"` ie. `15.9.14+28307.770`
4. Rename the instance folder to be `"{Edition}-{catalogInfo.productSemanticVersion}"` ie. `professional-15.9.14+28307.770`
5. Send in the pull-request

## disclaimer

This approach is not officially supported my Microsoft. Any MSI/EXE shared components will still roll forward and older versions cannot be side-by-side installed. See https://twitter.com/mrhestew/status/1137072701867061248
