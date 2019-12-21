## Project Structure

Currently, front-end consists of 5 main projects as below;

| Project | Contents | Dependencies |
|--|--|--|
| Core | Types, Interfaces, Models | - |
| Components | Directives, Components | Core |
| Api | Entities, Api Services | Core |
| Web | Pages | Core, Components, Api |
| Web-e2e | e2e tests for Web | Web |

## Color Palette

Cemiyet uses [tailwindcss](https://tailwindcss.com) framework and it comes with [default color palette](https://tailwindcss.com/docs/customizing-colors/#default-color-palette).

In addition, applications own palette which extends default palette;

| Preview | Name | HEX |
|--|--|--|
| <div class="palette-color" style="background-color:#61efce"></div> | Aquamarine | #61efce |
| <div class="palette-color" style="background-color:#efdab9"></div> | Champagne | #efdab9 |
| <div class="palette-color" style="background-color:#81c08b"></div> | De York | #81c08b |
| <div class="palette-color" style="background-color:#584b4f"></div> | Don Juan | #584b4f |
| <div class="palette-color" style="background-color:#3d3a3a"></div> | Eclipse | #3d3a3a |
| <div class="palette-color" style="background-color:#78b0a0"></div> | Gulf Stream | #78b0a0 |
| <div class="palette-color" style="background-color:#ffd152"></div> | Kournikova | #ffd152 |
| <div class="palette-color" style="background-color:#ff9900"></div> | Orange Peel | #ff9900 |
| <div class="palette-color" style="background-color:#8e8373"></div> | Schooner | #8e8373 |
| <div class="palette-color" style="background-color:#494236"></div> | Space Shuttle | #494236 |
| <div class="palette-color" style="background-color:#343233"></div> | Toledo | #343233 |
| <div class="palette-color" style="background-color:#ffc31f"></div> | Turbo | #ffc31f |
| <div class="palette-color" style="background-color:#45edc6"></div> | Turquoise | #45edc6 |
| <div class="palette-color" style="background-color:#efeae1"></div> | White Line | #efeae1 |

## Components

**Following is first draft for the components list that subject to change.**

Components under main component module;

- Button Group
- Card
- Collapsible
- Editable Text
- Outline
- Progress Bar
- Spinner
- Table

Components under their own module;

- DateTime
    - Date
    - Date Range
    - Time
- Elements
    - Button
    - Divider
    - Icon
    - Tag
    - Text
- Forms
    - Controls
        - Label
        - Checkbox
        - Radio
        - Select
        - Slider
        - Switch
    - Inputs
        - File
        - Number
        - Tag
        - Text
        - Text Area
- Navigations
    - Breadcrumb
    - Menu
    - Navbar
    - Tabs
    - Tree
- Overlays
    - Alert
    - Context Menu
    - Dialog
    - Drawer
    - Popover
    - Toast
    - Tooltip

<style>
    .palette-color {
        width: 2rem;
        height: 2rem;
        border-radius: 0.25rem;
    }
</style>
