# VSCode

![[VSCode.png]]
[VSCode Documentation](https://code.visualstudio.com/docs)

[VSCode Github](https://github.com/microsoft/vscode)

Download from [Microsoft Store](https://apps.microsoft.com/store/detail/XP9KHM4BK9FZ7Q) or [Web](https://code.visualstudio.com/)

## Settings.json

```json
{
  "editor.inlineSuggest.enabled": true,
  "[jsonc]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "terminal.integrated.fontFamily": "CaskaydiaCove Nerd Font Mono",
  "terminal.integrated.cursorStyle": "line",
  "editor.fontFamily": "Cascadia Code, Fira Code, Inter",
  "[blade]": {
    "editor.defaultFormatter": "onecentlin.laravel-blade"
  },
  "git.confirmSync": false,
  "[javascript]": {
    "editor.defaultFormatter": "esbenp.prettier-vscode"
  },
  "[markdown]": {
    "editor.defaultFormatter": "yzhang.markdown-all-in-one"
  },
  "[html]": {
    "editor.defaultFormatter": "vscode.html-language-features"
  },
  "editor.fontLigatures": true,
  "explorer.confirmDelete": false,
  "terminal.integrated.gpuAcceleration": "on",
  "window.commandCenter": true,
  "editor.minimap.enabled": false,
  "editor.renderWhitespace": "none",
  "workbench.colorTheme": "Parsinta Request",
  "workbench.iconTheme": "material-icon-theme",
  "liveServer.settings.donotVerifyTags": true,
  "liveServer.settings.donotShowInfoMsg": true,
  "php.suggest.basic": false,
  "php.validate.enable": false,
  "emmet.excludeLanguages": ["markdown", "php"],
  "[php]": {
    "editor.defaultFormatter": "bmewburn.vscode-intelephense-client"
  },
  "workbench.activityBar.visible": false,
"window.menuBarVisibility": "compact",
"window.zoomLevel": 1,
"editor.lineHeight": 2
}
```
## Extensions
-   PHP Intelephense
-   Laravel Artisan
-   Laravel Snippets
-   Laravel Blade Snippets
-   Laravel Blade Spacer
-   Laravel GoTo View

## Fonts
- [Cascadia Code](https://github.com/microsoft/cascadia-code)
## Color Theme
- [Parsinta](https://marketplace.visualstudio.com/items?itemName=Parsinta.parsinta-exclusive)
## File Theme
- [Material Icon Theme](https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme)
## Activate Command `Code .` in Terminal
- Open VSCode
- Click `Ctrl + Shift + P`
- Type `Shell`
- Select `Shell Command: Install 'code' command in PATH`