# webform_civicrm_esign

Module to work with the drupal esign module and add the signature as a file to a CiviCRM activity.

## Requirements
Does not work with CiviCRM 4.7.20 (a blank file is generated). Tested with CiviCRM 4.7.29, some earlier versions may work!.

## Setup
Download and install webform_civicrm and webform_civicrm_esign and webform_esign

## Usage
For each webform that you want to save the signature to an activity you need:

#### In CiviCRM:

* An activity type with a "File" custom field.

#### On each webform:

* A field of type "esign".
* A field with name: esign_custom_field, type: hidden, value: custom field name (eg. custom_9).
* A field with name: esign_activity_type_id, type: hidden, value: activity type id (eg. 70).

Make sure CiviCRM processing is enabled on the webform and that you have added one activity with the type you specified in esign_activity_type_id field.

Optionally, file the activity on a case by enabling a Case within the CiviCRM processing and setting the Activity to "File on Case". 