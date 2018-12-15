# xcg
An X4 mod in the workings. We want to make the economy deeper by adding a whole consumer goods industry.

## Development Guide

### XML Patching

XMLPatching is only necessary if you need to go deep.  You can write the xml without patching if you are adding to a list that is not deeply nested.

### Adding a new ware

Please consider every mentioning of `{WARE_ID}` to be replaced of what ware we want to add, and it must be lowercase to ensure compatibility across systems. 
Generally, we will be prefixing every ware we add with `xcg_` - to avoid any collision issues with other mods.

**NOTE:** Please make sure the file is lowercase and does not contain any whitespace characters (space)

### Create new assets

To add a ware and the production of the ware to the game, the following files need to be created from scratch:

<table>
<thead>
    <tr>
        <th>File Path</th>
        <th>Description</th>
    </tr>    
</thead>
<tbody>
  <tr>
    <td><code>assets/fx/gui/textures/xcg_{WARE_ID}_macro.dds</code></td>
    <td>A 256x256x 2D image encoded as a <strong>dds texture</strong> that is presented to the user in the Station Build interface.</td>
  </tr>
  <tr>
    <td><code>assets/structures/production/macros/xcg_{WARE_ID}_macro.xml</code></td>
    <td>Contains some of information about the <strong>station production module</strong> of this ware. specifically the hull strength, maximum workforce, explosive radius when destroyed, and what ware it creates.  It does NOT contain more information about the ware itself, such as production costs.
    </td>    
  </tr>
  <tr>
    <td><code>assets/wares/macros/xcg_{WARE_ID}_macro.xml</code></td>
    <td>Contains very limited information about the ware itself, seems to be <strong>boilerplate</strong> code. but it has to exist.  You can copy and paste all the code from an existing wares macro into this one, changing only its name</td>
  </tr>
</tbody>
</table>

---

### Include the new assets

The following files need to be modified to "wire up" your ware to the game.  If these are not modified, the game will not even load your new assets.

**NOTE:** Any mention of path in these files must include `extensions/XCG/` prefixed before the rest of the path.

<table>
<thead>
    <tr>
        <th>File Path</th>
        <th>Description</th>
    </tr>    
</thead>
<tbody>
  <tr>
    <td><code>index/macros.xml</code></td>
    <td>A manifest of all macros that do not normally exist in the game (new additions).  For every ware and every production module you add, you must put them in here or the game will NOT load them.</td>
  </tr>
  <tr>
    <td><code>index/components.xml</code></td>
    <td>OPTIONAL: If you are creating your own models for the macros to use, we currently are not doing this.</td>
  </tr>
  <tr>
    <td><code>libraries/icons.xml</code></td>
    <td>This tells the game to load your texture for <strong>station production module></strong> interface.  You will need to point it to the texture file you add in <code>fx/gui/textures/</code></td>    
  </tr>  
</tbody>
</table>

---

### Update existing files

These files are relatively easy to operate on, simply add your new entry to each of them, following the same pattern you copy from a previous existing one.

<table>
<thead>
    <tr>
        <th>File Path</th>
        <th>Description</th>
    </tr>
</thead>
<tbody>
  <tr>
    <td><code>libraries/baskets.xml</code></td>
    <td>An xml patch file that specifies what categories this ware belongs.  It isnt certain how this is used by the game exactly, but we suspect it is used by traders in jobs.xml to determine which goods they trade. So we can be more specific there.</td>
  </tr>  
  <tr>
    <td><code>libraries/modulegroups.xml</code></td>
    <td>Exact game usage of this is unknown. Seems to be mostly boilerplate about the station module that produces the ware, you can mostly copy paste what you see in our existing list, changing just the fields about the name and id, description, etc.
    </td>
  </tr>
  <tr>
    <td><code>libraries/modules.xml</code></td>
    <td>Exact game usage of this is unknown. Seems to be mostly boilerplate about the station module that produces the ware, you can mostly copy paste what you see in our existing list, changing just the fields about the name and id, description, etc.
    </td>
  </tr>
  <tr>
    <td><code>libraries/wares.xml</code></td>
    <td>Contains majority of the metadata about the ware, it also includes the entry for the blueprint that is required to unlock the ware.
    </td>
  </tr>    
</tbody>
</table>
