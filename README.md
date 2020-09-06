# logbook
AnaestheticsApp Logbook

# Changing configuration files
* If you want to improve the options of the logbook, you can now edit the configuration files.
* All changes will be reviewed and, if approved, will be added with the next logbook update.

### ```./config/logbook-config.mjs```
* This file contains the form options for adding/editing cases
* The items in each object or array are in UPPERCASE and will be replaced on build time by the corresponding item found in ```./lang/en/form.js``` and ```./lang/de/form.js```.
  * Therefore, when adding an item, this must be in UPPERCASE and must be added to ```./lang/en/form.js``` and ```./lang/de/form.js```.
* It contains the following variables:

```js
// default specialities shown when no cases have been added to the current work place
export const commonSpecialities = [...];

// list of all specialities that can be selected
export const specialities = [...];

// list of all modules
export const modules = [...];

// contains the form options for each form field
export const lists = [...];

// specific to Uganda
export const listsUganda = [...];

// items displayed when a specifies speciality is selected
export const listsSmart = [...];

// specific to Uganda
export const listsSmartUganda = [...];

```

### Example
* To add a new item called "Adductor canal block", open ```./config/logbook-config.mjs```
```js
export const lists = {
  ...,
  regionalPeripheral: [
    FORM.INTERSCALENE,
    FORM.SUPRACLAVICULAR,
    FORM.INFRACLAVICULAR,
    FORM.AXILLARY,
    FORM.FEMORAL,
    FORM.SCIATICA,
    FORM.FASCIA_ILIACA,
    FORM.POPLITEAL,
    FORM.ANKLE,
    FORM.ADDUCTOR_CANAL, // this is the item we are adding, items above are already present in the logbook
  ],
}
```
* Now add this to ```./lang/en/form.js``` and ```./lang/de/form.js```
* If you add an English item, just leave the German one empty, unless you know the German translation! (and vice versa)
* You must add your item to both the English and German language files, otherwise the app won't build!
* Ideally, add the item in alphabetical order to avoid duplicates
```js
// Editing the English file in /lang/en/form.js
const FORM = {
  ...,
  FORM.ADDUCTOR_CANAL: 'Adductor canal block',
}

// Editing the German file in /lang/de/form.js
const FORM = {
  ...,
  FORM.ADDUCTOR_CANAL: '', // leave empty unless you know the German translation
}
```
