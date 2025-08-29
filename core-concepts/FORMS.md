---
title: 'Forms'
icon: 'text-cursor-input'
---

## Introduction

The Form Builder is a powerful tool that allows you to create custom forms for collecting data from your users. This guide will walk you through the process of creating, customizing, and publishing forms.

## Getting Started

### Creating a New Form

1. Navigate to the Forms section in the sidebar.
2. Click the "Create Form" button.
3. Enter a name for your form in the "Name" field.
4. Add an optional description to provide context for your form.
5. Select the visibility option:

* Private: Only members of your organization can access the form
* Public: Anyone with the link can access the form

## Building Your Form

<figure><img src="https://3431340728-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FsU4OKsizzEpCVNSoTs7U%2Fuploads%2FUGn44NNCJIhAraiwsF9m%2FScreenshot%202025-08-23%20at%2010.56.50%E2%80%AFPM.png?alt=media&#x26;token=ec70ecba-29ec-4fd8-b6e4-44073afd8e63" alt=""><figcaption></figcaption></figure>

### **Adding Elements**

1. Navigate to the "Builder" tab (selected by default).
2. From the left panel, select an element type from the dropdown:

* Text Input: For collecting short text responses
* Email Input: For collecting email addresses
* Number Input: For collecting numerical data
* Checkbox: For yes/no or agreement questions
* Dropdown: For selecting from a list of options
* Radio Group: For selecting one option from a list
* Text Area: For collecting longer text responses
* File Upload: For collecting files
* Header: For adding section titles
* Paragraph: For adding explanatory text
* Divider: For visually separating sections

1. Click the "+" button to add the selected element to your form.

### **Organizing Elements**

Each element in your form can be:

* Moved up: Click the up arrow button to move an element higher in the form
* Moved down: Click the down arrow button to move an element lower in the form
* Removed: Click the trash icon to delete an element from your form

### **Configuring Elements**

1. Click on any element in the canvas to select it.
2. The properties panel on the left will update to show options for that element:

* ID: A unique identifier for the element (used when processing form data)
* Label: The text shown to users above the input field
* Placeholder: Example text shown inside the input field
* Required field: Toggle this checkbox to make the field mandatory

### **Working with Options (Dropdown and Radio Group)**

For elements that have options (Dropdown and Radio Group):

1. Select the element in the canvas.
2. In the properties panel, you can:

* Choose from predefined option sets (Yes/No, Days of Week, Months, etc.)
* Add custom options by clicking the "Add" button
* Clear all options by clicking the "Clear" button
* Edit option labels and values individually
* Remove specific options using the trash icon

### Previewing Your Form

1. Click the "Preview" tab to see how your form will appear to users.
2. The preview shows all your form elements as they will appear when published.
3. You can interact with the form elements, but submissions are disabled in preview mode.

### Form Settings

1. Click the "Settings" tab to configure your form's general settings.
2. Here you can modify:

* Form name
* Form description
* Visibility (Private or Public)

### Saving Your Form

1. Click the "Save" button in the top-right corner to save your changes.
2. A success notification will appear when your form is saved successfully.

### Publishing Your Form

1. Once your form is ready, click the "Publish" button in the top-right corner.
2. Publishing makes your form accessible to users according to your visibility settings.
3. You can unpublish the form at any time by clicking the "Unpublish" button.

### Sharing Your Form

After publishing your form:

1. A form link will appear at the top of the page and in the Settings tab.
2. Click the "Copy" button to copy the link to your clipboard.
3. Share this link with your intended audience.
4. Note: If your form is set to "Private," only members of your organization can access it.

### Working with Form Submissions

When users submit your form:

1. The data is collected and stored securely.
2. If the form is connected to a workflow, the submission will trigger that workflow.
3. Form data is passed as variables to the workflow, with each field's ID as the variable name.
