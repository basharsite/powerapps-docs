
<properties
    pageTitle="Card control: reference | Microsoft PowerApps"
    description="Information, including properties and examples, about the Card control"
    services=""
    suite="powerapps"
    documentationCenter="na"
    authors="gregli-msft"
    manager="erikre"
    editor=""
    tags=""/>

<tags
   ms.service="powerapps"
   ms.devlang="na"
   ms.topic="article"
   ms.tgt_pltfrm="na"
   ms.workload="na"
   ms.date="02/29/2016"
   ms.author="gregli"/>

# Card control in PowerApps #
Provides the display and editing experience for a single field of a **Display form** or **Edit form** control.

## Description ##
**Display form** and **Edit form** controls act as containers for displaying and viewing entire records. Each container can hold a set of **Card** controls that display individual fields or provide a way to update those fields. Each card has a **DataField** property that specifies which field of the record it works on.  

Predefined cards are defined for different data types and user experiences.  For example, there may be a card to edit a number field with a **Text input** control, which is great for use with the keyboard. Another card might support editing a number by using a **Slider** control instead. With the form control selected and the **Options** pane open, you can easily select a card based on a field.

Cards themselves contain controls. The controls of a card make up the experience for displaying and editing a single field. For example, a number card may consist of a **Text box** control to provide the display name of the field and a **Text input** control to provide an editor for the value of the field. The card may also have a **Text box** control that shows any validation errors that occur and a **Text box** control for the common asterisk to indicate that a field is required.

You can customize the controls of a predefined card by resizing it, moving it, hiding it, adding controls to it, and making other changes. You can also start with an entirely blank card, a "custom card", to which you add controls from scratch.

Predefined cards are *locked* by default. In a locked card, you can modify only certain properties of the card or the controls within the card, and you can't delete a locked card. You can show the card lock and unlock it on the **View** tab of the **Advanced** view. If a property is locked and can't be modified, it appears with a lock icon next to its name. Unlocking a card is an advanced activity and should be done with care, because automatic formula generation will no longer occur for the card, and you can't relock a card.

Within the form's container, the **ThisItem** record is available and contains all the fields of the record.  For example, the card's **Default** property is often set to **ThisItem**.*FieldName*.

You can use the **Parent** reference to configure a control to reference the properties of a card.  For example, a control should use **Parent.Default** to read the initial state of the field from the data source. By using **Parent** instead of directly accessing the information that you want, the card is better encapsulated, and you can change it to a different field without breaking internal formulas.

See [Understand data cards](working-with-data-cards.md) for examples of how to customize, unlock, and create cards.

## Key properties ##
**DataField** – The name of the field within a record that this card displays and edits.

- Specify the name as a single static string that's enclosed in double quotation marks (for example, **"Name"**), not a formula.
- Unbind a card by setting its **DataField** property *blank*. The **Valid** and **Update** properties are ignored for unbound cards.

[**Default**](properties\properties-core.md) – The initial value of a control before the user changes it.

- For each control in a card, set this property to **Parent.Default** to refer to the default value of the field according to the data source. For example, set a slider's **Default** property to **Parent.Default** to ensure that the user starts with a generic value for that slider.

**DisplayName** – The user-friendly name for a field in a data source.

- The **DataSourceInfo** function provides this metadata from the data source.
- Controls within the card should use **Parent.DisplayName** to refer to the name of the field.

**Error** – The user-friendly error message to display for this field if validation fails.

- This property is set when **SubmitForm** is called.  
- The message describes validation problems based on the data source's metadata and checking the card's **Required** property.

**Required** – Whether the user must specify a value for this field when editing or creating a record.

- The **DataSourceInfo** function provides the required metadata from the data source.
- Controls within the card should use **Parent.Required** to determine whether that card's field is required.

**Update** – The value to write back to the data source for a field.

- Use this property's formula to pull the values from the edit controls of the card in order to write back to the data source. For example, set a card's **Update** property to **Slider.Value** to update the data source with a value from the slider in that card.

## Additional properties ##

[**BorderColor**](properties\properties-color-border.md) – The color of a control's border.

[**BorderStyle**](properties\properties-color-border.md) – Whether a control's border is **Solid**, **Dashed**, **Dotted**, or **None**.

[**BorderThickness**](properties\properties-color-border.md) – The thickness of a control's border.

[**Fill**](properties\properties-color-border.md) – The background color of a control.

[**Height**](properties\properties-size-location.md) – The distance between a control's top and bottom edges.

**Valid** – Whether a **Card** or **Edit form** control contains valid entries, ready to be submitted to the data source.

[**Visible**](properties\properties-core.md) – Whether a control appears or is hidden.

[**Width**](properties\properties-size-location.md) – The distance between a control's left and right edges.

[**X**](properties\properties-size-location.md) – The distance between the left edge of a control and the left edge of the screen.

[**Y**](properties\properties-size-location.md) – The distance between the top edge of a control and the top edge of the screen.

## Examples ##

See [**Understanding data cards**](working-with-data-cards.md) for examples.