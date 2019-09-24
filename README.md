# webform_civicrm_esign

Module to work with the drupal esign module and add the signature as a file to a CiviCRM activity.

![Example](screenshot.png)

## Requirements
Does not work with CiviCRM 4.7.20 (a blank file is generated). Tested with CiviCRM 4.7.29, some earlier versions may work!.

## Setup
Download and install:
- webform_civicrm (https://www.drupal.org/project/webform_civicrm).
- Signature Pad library (https://github.com/szimek/signature_pad) (Release v2.3.0 - v3.0 does not get detected correctly by Drupal).
- esign (https://www.drupal.org/project/esign).
  - Requires webform_validation.
  - Enable modules esign and esign_webform.
  Note: If you want to disable the "signer name" and "signer title" fields on the esign field you need to use this patched version of the drupal esign module which adds checkboxes to the "esign" field type: https://github.com/mattwire/drupal_esign
- webform_civicrm_esign (https://github.com/mattwire/webform_civicrm_esign)

## Usage
For each webform that you want to save the signature to an activity you need:

#### In CiviCRM:

* An activity type with a "File" custom field.

#### On each webform:

* A field of type "esign".
* A field with name: esign_custom_field, type: hidden, value: Comma separated list of custom field IDs
  - Example: A single custom field on a single activity: custom_9
  - Example: A single custom field on multiple activities (different types): custom_9,custom_9
  - Example: Two custom fields on a single activity: custom_9,custom_10
  - Example: Different custom fields on different activities (different types): custom_9,custom_10
* A field with name: esign_activity_type_id, type: hidden, value: Comma separated list of Activiy Type IDs
  - Example: A single activity: 70
  - Example: Multiple activities: 70,71
  - **Warning: Currently multiple activities of the same activity type in one form are not supported**
* Make sure CiviCRM processing is enabled on the webform and that you have added one activity with the type you specified in esign_activity_type_id field.

Optionally, file the activity on a case by enabling a Case within the CiviCRM processing and setting the Activity to "File on Case".

* Filenames will be created in the format "sig_20191119000000_firstnamelastname.png" if civicrm firstname/lastname fields are found.  If not name will be omitted.
* esign_custom_field and esign_activity_type_id will not be shown in emails / submission views.
