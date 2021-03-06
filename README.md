# MultiDateField module

Provides an MultipleDatePickerField for managing and saving a string of multiple dates into a text field. Integrates [jQuery MDP plugin](https://github.com/dubrox/Multiple-Dates-Picker-for-jQuery-UI), a plugin that enables jQuery UI calendar to manage multiple dates. See [demo of the javascript interface & configuration options](http://multidatespickr.sourceforge.net/).

## Maintainer Contact

 * Michael van Schaik <mic (at) restruct (dot) nl>

## Requirements

 * SilverStripe 3.0 or newer

## Features

  * Builds on silverstripe DateField (with Text field), same config & localisation supported (specific locales may need some further testing)
  * Integrates [MDP 1.6.3](https://github.com/dubrox/Multiple-Dates-Picker-for-jQuery-UI), a plugin that enables jQuery UI calendar to manage multiple dates
  * Allows setting custom date separator (default: ", "), more Multidatepicker-specific configuration options can easily be added.
  * TODO(!): I could use some help with the silverstripe config system for this module; I'm now using ($this->getConfig('separator') ? $this->getConfig('separator') : ', ') in order to provide a callback for the date separator because sometimes custom configuration values don't seem to load.
  * TODO: Saving into many_many relation (currently only textfield supported)
  * TODO: Full unit test coverage
  * TODO: Validation (currently commented out)

## Usage

### Dates as Textfields

Event Model

	class Event extends DataObject {
		static $db = array(
			'Dates' => 'Text'
		);
	}

Formfield Instantiation:

	$md = new MultiDateField('Dates');
		$md->setConfig('dateformat', 'dd-MM-yyyy');
		$md->setConfig('showcalendar', true);
		$md->setConfig('separator',' & ');
