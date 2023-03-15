[![Build Status](https://travis-ci.org/adiwg/mdCodes.svg)](https://travis-ci.org/adiwg/mdCodes)
[![Gem Version](https://badge.fury.io/rb/adiwg-mdcodes.svg)](http://badge.fury.io/rb/adiwg-mdcodes)
[![Bower version](https://badge.fury.io/bo/mdcodes.svg)](https://badge.fury.io/bo/mdcodes)
[![npm version](https://badge.fury.io/js/mdcodes.svg)](https://badge.fury.io/js/mdcodes)

# mdCodes

mdCodes provides code lists in hash or JSON formats for loading of mdEditor and other metadata
tools that use the ADIwg [mdJson-schemas](https://github.com/adiwg/mdJson-schemas).  The code lists
include all ISO 19115-2 and ISO 19115-1 codes plus supplemental codes added by NGDC and ADIwg. The
code lists may be accessed in Ruby using the gem. Alternatively, JSON may be generated from the YAML
using [Grunt](http://gruntjs.com/getting-started). Bower and NPM packages are available as well.
See the following for instructions.

## Bower

    bower install mdcodes

## npm

    npm install mdcodes

**Note:** The npm install will also create JavaScript modules for the codelists.

## Ruby

The adiwg-mdcodes gem provides code lists in Ruby hash or JSON formats.

### Installation

Add this line to your application's Gemfile:

    gem 'adiwg-mdcodes'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install adiwg-mdcodes


### Methods

#### getYamlPath
> returns the path to the 'resources' folder containing codelist files in YAML format'.

#### getAllCodelistsDetail( returnFormat )
> returns all code lists with all codelist detail
> returnFormat = \[__hash__ | json] (string)

#### getCodelistDetail( codeListName, returnFormat )
> returns a single codelist with all code list detail
> codeListName = name of code list to return (string)
> returnFormat = \[ __hash__ | json ] (string)

#### getAllStaticCodelists( returnFormat )
> returns all static codelists with only the codelist item names
> returnFormat = \[__hash__ | json] (string)

#### getStaticCodelist( codeListName, returnFormat )
> returns a single static codelist with only the codelist item names
> codeListName = name of code list to return (string)
> returnFormat = \[__hash__ | json] (string)

##Grunt

Generate JSON verions of the code lists using Grunt.

**Note**: These instructions assume that [npm](https://docs.npmjs.com/) and [Grunt](http://gruntjs.com/getting-started) are already installed. The generated
files are not tracked by git.

1. Change to the project's root directory.
2. Install project dependencies with ```npm install```.
3. Generate the JSON code lists with ```grunt```.
4. The JSON is written to the *resources/json* directory.

# Contributing

1. Fork it (https://github.com/adiwg/mdCodes/fork)
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create a new Pull Request


## ISO codelist creation guidelines

The following guidelines apply when creating new codelists that are based on ISO maintained sources (e.g. [codelists.html](https://standards.iso.org/iso/19115/resources/Codelists/cat/codelists.html), [codelists.xml](https://standards.iso.org/iso/19115/resources/Codelists/cat/codelists.xml)). The ISO "CI_DateTypeCode" codelist will be used as an example to illustrate the guidelines for creating codelist attributes.

### `codelistName`

  1. Identify the desired ISO codelist name (e.g. "[CI_DateTypeCode](https://standards.iso.org/iso/19115/resources/Codelists/cat/codelists.html)")
  2. Remove class identifier prefix and "Code" suffix (CI_DateTypeCode -> DateType)
  3. Convert shortened name to lowerCamelCase and add "iso_" prefix (= iso_dateType)
  4. CI_DateTypeCode: `codelistName` = iso_dateType
  5. Use the newly created `codelistName` as the file name (e.g. [**iso_dateType.yml**](https://github.com/adiwg/mdCodes/blob/master/resources/iso_dateType.yml))

### `source`

  1. Use value "ISO"

### `sourceName`

  1. Use the ISO specified codelist name. See the `<cat:name>` element from [codelists.xml](https://standards.iso.org/iso/19115/resources/Codelists/cat/codelists.xml) snippet below:


  > <cat:CT_Codelist id="CI_DateTypeCode">
  > \<cat:codelistItem>
  > \<cat:identifier>
  > <gco:ScopedName codeSpace="http:\/\/standards.iso.org/iso/19115/-3/cit/1.0">CI_DateTypeCode</gco:ScopedName>
  > </cat:identifier>
  >> \<**cat:name**>
  >> <gco:ScopedName codeSpace="http:\/\/standards.iso.org/iso/19115/-3/cit/1.0">**`CI_DateTypeCode`**</gco:ScopedName>
  >> </**cat:name**>

  2. `sourceName` = "CI_DateTypeCode"

### `description`
  1. Use the ISO specified codelist description
  2. `description` = "identification of when a given event occurred"

