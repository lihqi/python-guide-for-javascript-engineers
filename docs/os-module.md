---
id: os-module
slug: /os-module
title: OS Module
sidebar_label: OS Module
---

The `os` module in Python provides functions for manipulating files and directories, as well as accessing system-related information.

### Task

Write a program to list all the files and directories in a given directory. The program should print the name of each item and indicate whether it is a file or a directory.

#### JavaScript implementation
```javascript
import fs from 'fs';
import path from 'path';

function listItems(directory) {
  fs.readdir(directory, (err, items) => {
    if (err) {
      console.log(`Error reading directory: ${err}`);
      return;
    }

    items.forEach((item) => {
      const itemPath = path.join(directory, item);
      fs.stat(itemPath, (err, stats) => {
        if (err) {
          console.log(`Error getting information for ${item}: ${err}`);
        } else {
          console.log(`${item}: ${stats.isDirectory() ? 'directory' : 'file'}`);
        }
      });
    });
  });
}

listItems('../');
```

#### Python implementation
```python
import os

def list_items(directory):
    items = os.listdir(directory)

    for item in items:
        item_path = os.path.join(directory, item)
        if os.path.isdir(item_path):
            print(f"{item}: directory")
        else:
            print(f"{item}: file")

list_items('../')
```

### Difference Quick View

| Feature | JavaScript | Python |
|---------|------------|--------|
| Check if file or directory exists | fs.existsSync(path) | os.path.exists(path) |
| Create directory | fs.mkdir(path, [options], callback) | os.mkdir(path) |
| List directory | fs.readdir(path, [options], callback) | os.listdir(path) |

### Resources

- https://docs.python.org/3/library/os.html
