# README

This is the GitHub repository for Microsoft Edge documentation for http://dev.modern.ie

At the mooment, both MS Edge and IE developer content still live in MSDN Library at https://msdnstage.redmond.corp.microsoft.com/en-us/library/hh772401(v=vs.85).aspx
We are working to port the MS Edge-related topics and resources here, as well as exclusively author any new content (e.g., extensions) here.

TODO: 
* Contributing guide
* License
* 

## Instructions / Format for adding new Docs and Links

  - Docs are grouped by folders
  - A folder can contain more folders or a readme.md
  - One .md file per folder
  - Folder/directory names should be dash-separated (ie. f12-tools) as they will be directly used for documentation URLs on the Microsoft Edge Dev site ---- NOT underscore (ie. f12_tools) or PascaleCase/camelCase (ie. f12Tools). 
  - Links should be formatted as: ../Perfomance/  (not ../Perfomance/ReadMe.md)
  - Section headers should use a standard syntax of a space after hashes, formatted as  ## Section Heading *(not ##Section Heading)*. Otherwise markdown is not being parsed correctly when pulled into the Microsoft Edge Dev site.
  - For a guide to writing GitHub Markdown: https://guides.github.com/features/mastering-markdown/
:octocat:
  - *Include a License.md in your Repo*
  >[Info about Licensing on GitHub](https://help.github.com/articles/open-source-licensing/)

Example: 
>*Copyright (c) Microsoft Corporation. All rights reserved.*

>*Licensed under the Apache License, Version 2.0 (the "License"); you may not use these files except in compliance with the License. You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0*

>*Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.*

**File Structure should look like...**

![Edge Documentation File Structure](./f12_guide/media/github_doc_filestructure.PNG)


##Testing Animated GIF feature for demo documentation purposes
![Edge Animated Gif Test](/f12_guide/media/EdgeDevToolsGIF_Test.gif)
