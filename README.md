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


        typescript :
        create a desc.d.ts file in your project root folder and add this line :
        declare module "zipcelx-on-steroids"
          
## Issues
Should it happen that the tool broke down on you please head to our [Issue tracker](https://github.com/davidramos-om/zipcelx-on-steroids/issues)
1. Search if the issue is already discussed or explained.
2. If no luck feel free to open a new issue and we will get back to you as soon as possible.
