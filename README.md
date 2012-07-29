StarlingCodea
=============

StarlingCodea is a lua porting for [Codea](http://twolivesleft.com/Codea/) of the AS3 
[Starling Framework](http://gamua.com/starling/) developed by Gamua OG. Starling itslef is the AS3 port of 
[Sparrow](http://gamua.com/sparrow/), the Objective-C 2D framework developed always by Gamua OG. 

StarlingCodea is a 2D framework that mimes the DisplayList of Adobe Flash/Flex, letting developer used to work
with AS3 to easily move to Codea and Lua.

It offers:

- A complete displayList optimized for bitmap rendering (through codea meshes and texture atlas) including:
  - DisplayObj
  - DisplayObjContainer
  - Stage
  - Quad
  - Image
  - MovieClip
  - Button
- Animation facilities
- Texture and Texture Atlas support, including [TexturePacker](http://www.codeandweb.com/) file parsing
- A full tweening library
- EventHandling
- Basic Touch Managament with drag and drop support

Contents
--------

- ExternalLibs.codea: Set of 3rd part libs used by StarlingCodea
- Starling.codea: the main lib of the project
- StarlingExamples: data files for StarlingExamples.codea
- StarlingExamples.codea: a repository of examples for different StarlingCodea features
- StarlingTween.codea: the StarlingCodea Tween library
- Utils.codea: Several utilities used by StarlingCodea, like filesystem, xmlNode, math functions ecc.
- LuaSandbox.lua: required to unsandbox codea lua environment and enable feature like libraries import and load/write of generic files

How to Install
--------------

The default installation requires to overwrite Codea luaSandbox.lua file with the one provided that removes all 
restrictions on what Codea programs can do. That's needed to enable 
[import functionality between projects](http://twolivesleft.com/Codea/Talk/discussion/1087) (thanks to Rui Viana) 
and to support generic file read/write (like xml files). 

Moreover the StarlingExamples.codea project is configured to look for the StarlingExamples data file directory 
as subfolder of Dropbox Codea sync folder (NB: even if Codea doesn't shows subfolders or non png files in the Dropbox browser 
panel, the subfolders are correctly synched and browsed by the file system)

It's possible anyway to run the example putting data files in other places, including creating a 
[custom spritepack](https://bitbucket.org/TwoLivesLeft/codea/wiki/com.twolivesleft.Codify). Please refer to 
Utils/IO.lua file for more infos about file system support and configuration in sandboxed and unsandboxed environments.

It's also possibile to use StarlingCodea in a sandboxed environment but that has 2 great limit:

1. Codea support for lib dependencies (available from 1.4.3) is not recursive and so all the libs must be collapsed 
into a single project (that has to be done manually)

2. Codea doesn't support load of generic files so even if it's still possibile to load images from dropbox, 
documents or spritepacks, for other files like xml there's no chance. The only way is to convert them in lua 
files and add them to projects. For that reason StarlingCodea Texture Packer support includes not only a parser 
for Sparrow/Starling xml file format, but also one for [Moai](http://getmoai.com/) lua file format.