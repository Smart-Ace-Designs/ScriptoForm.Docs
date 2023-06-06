# Control Pair placement with snippet hints
In a [[Index|ScriptoForm]], most controls come as a pair (an interactive control, such as a text box or combo box, and its partner label control) and these are collectively know as a *control pair*.  A standard ScriptoForm is designed such that:

- The vertical space between controls in a control pair is always **20** units
- The vertical space between control pairs is always **35** units

![[ControlPairUnits.png]]

The [Visual Studio Code snippets JSON](https://github.com/Smart-Ace-Designs/SmartAceDesigns.ScriptoFormTemplates/tree/main/VSCode) file takes advantage of this standardization by including hints in the "Location" properties of control pairs to help you properly place them on the form.  As you tab through the control pair snippet, you will eventually land on the "hint" for the height property at which time you will need to provide a value based on the control pair you adding: the height of a label is always in relation to the previous control pair above it and the height of the interactive control is always in relation to its partner label control.

## The "15|P+35" hint
This hint it typically used to determine the height of the label in a control pair:
>When adding the very first control pair to the form, use **15** for the height of the label
>For all other control pairs, use **35 plus the height of the previous interactive control** to determine the height of the new label control you are adding

## The "P+20" hint
This hint it typically used to determine the height of the interactive control in a control pair:
>Use 20 plus the height of its partner label control

## The "P-1" hint
This hint is unique to the "Label & TextBox & Search Button" control *group*, which has three controls in it.  The search button in this group is usually 1 unit less than the height of the textbox it is adjacent to, for appearance purposes.

![[SearchButton.png]]

>Use 1 unit less than the height of its adjacent textbox control
