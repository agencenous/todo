# TODO

CLI utility to check TODOs comments in projects

## Installation

```bash
composer require --dev agencenous/todo
```

## Usage

```bash
vendor/bin/todo
```

By default, the command will search for `TODO:` comments in the current directory and its subdirectories in files with format: php, js, css, scss, jsx.

Some directories are excluded by default: `vendor`, `node_modules`, `cache`, `.git`.

You can override these settings by passing arguments to the command:

```bash
vendor/bin/todo path/to/directory --formats=php,js,css,scss,jsx --exclude=vendor,node_modules,cache,.git
```

For a more convenient use, you can also create a configuration file `.todo.json` at the root of your project:

```json
{
    "formats": ["php", "js", "css", "scss", "jsx"],
    "exclude": ["vendor", "node_modules", "cache", ".git"]
}
```

## Example

```bash
vendor/bin/todo
```
output (colorized):

```
./src/Controller/ApiController.php
- Line 422: "Apply pagination in query instead of post-processing"
./src/Front/components/DateView/index.js
- Line 7: "add format parameter to format the date"
./src/Helper/Apps/GoogleHelper.php
- Line 327: "Implete update event"
- Line 374: "Implete delete event"

 Found 4 TODOs 
```

If TODOs are found, the command will exit with status code 1, otherwise it will exit with status code 0.