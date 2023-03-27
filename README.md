zipcelx
=======

<p align="center">
  <a href="https://raw.githubusercontent.com/davidramos-om/zipcelx-on-steroids/master/LICENSE">
    <img src="https://img.shields.io/badge/License-MIT-yellow.svg" />
  </a>
  <a href="https://www.npmjs.com/package/zipcelx-on-steroids">
    <img src="https://img.shields.io/npm/v/zipcelx-on-steroids.svg" alt="version" />
  </a>
  <a href="https://www.npmjs.com/package/zipcelx-on-steroids">
    <img src="https://img.shields.io/npm/dt/zipcelx-on-steroids.svg" alt="downloads" />
  </a>
</p>

Generate XLSX files in the browser, with minimal footprint. The vision is to provide the smallest possible package for generating valid XLSX files in the browser.

If you're looking for advanced functionality, [js-xlsx](https://github.com/SheetJS/js-xlsx) is a solid choice.

Fork : https://github.com/egeriis/zipcelx

## Table of contents
1. [How to use](https://github.com/dixieio/zipcelx/wiki/How-to-use)
2. [The config object](https://github.com/dixieio/zipcelx/wiki/The-config-object)
3. [Contributing](https://github.com/dixieio/zipcelx/wiki/Contributing)

## New Features
* Pull requests from community added 
* now support action param  : 
    1. "export" : download as xlsx   
    2. "blob" : return a blob object so you can use it as you need.
* Support column width and style (The possible values for this attribute are defined by the W3C XML Schema unsignedInt datatype)
* Col format is described [here](https://msdn.microsoft.com/en-us/library/office/documentformat.openxml.spreadsheet.column. aspx)

## Config
[Look here in a meanwhile](https://github.com/egeriis/zipcelx/wiki/The-config-object) 

## Use
    
        import zipcelx from 'zipcelx-on-steroids'

        zipcelx(config,'export') to save as xlsx
        zipcelx(config, 'blob') to return a blob oject


TypeScript: @types/zipcelx-on-steroids
```typescript
  declare module "zipcelx-on-steroids" {

    export interface IConfig {
        filename: string;
        sheet: {
            data: any[][];
        };
    }

    export default function zipcelx(config: IConfig, target: 'export' | 'blob'): any;
}
```

## Example
```typescript
import zipcelx from 'zipcelx-on-steroids';
import download from 'downloadjs';

export type ExportColumn = {
    fieldName: string,
    format: string,
    value: string;
    type: string;
}

export function exportTo(filename: string, columns: ExportColumn[], data: any[], target: 'export' | 'blob') {
    generateFileStructure(filename, columns, data, target);
}

export function generateFileStructure(filename: string, columns: ExportColumn[], data: any[], target: 'export' | 'blob'): any {

    let info: Array<Array<any>> = [ [] ];

    columns.forEach((col: ExportColumn) => {
        info[ 0 ].push({ value: col.value, type: col.type });
    });

    data.forEach((item) => {
        let index = info.push([]);
        for (let [ , value ] of Object.entries(item)) {
            info[ index - 1 ].push({ value: value ? value : '', type: 'string' });
        }
    });

    const config =
    {
        filename: filename,
        sheet: {
            data: info,
        }
    };

    return zipcelx(config, target);
}

export function downloadFile(fileName: string, zipcelFile: any) {
    try {
        if (zipcelFile) {
            var x = new XMLHttpRequest();
            x.open("GET", `/${fileName}`, true);
            x.responseType = "blob";
            x.onload = function (e) {
                download(zipcelFile, fileName, "application/vnd.openxmlformats-officedocument.spreadsheetml.sheet");
            };
            x.send();
        };
    }
    catch (error) {
        console.log(error);
    }
}
```
          
## Issues
Should it happen that the tool broke down on you please head to our [Issue tracker](https://github.com/davidramos-om/zipcelx-on-steroids/issues)
1. Search if the issue is already discussed or explained.
2. If no luck feel free to open a new issue and we will get back to you as soon as possible.
