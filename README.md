# php-ical
PHP-iCal is a PHP class for generating simple ICS files

It is completely based on RFC5545, the iCal standard. It does NOT implement every feature but the most basic ones. 
Every one who's looking for a simple class i think is right here.

<pre>
# load class
require_once('class.ical.php');

# create new ical object
$ical = new iCal();

# then add a new event with all data you want, here is complete list of options you can set
$ical->NewEvent();
$ical->SetTitle("Hallo this is my first event"); => REQUIRED
$ical->SetDescription("Add more detailed text here");
$ical->SetDates("2013-02-14 20:15", "2013-02-14 22:15"); => REQUIRED
$ical->SetStatus("confirmed"); => default: confirmed (or: tentative/cancelled)
$ical->SetLocation("place to go");
$ical->SetAlarm();
$ical->SetAlarmText("here is your reminder message text");
$ical->SetAlarmTrigger(30); => minutes before event

# simply repeat the newevent method to create more than 1 job, here a very basic example
$ical->NewEvent();
$ical->SetTitle("this is my second event");
$ical->SetDates("2013-02-14 22:30", "2013-02-15 00:15");

# let's set up a third one with multiple alarms
$ical->NewEvent();
$ical->SetTitle("my third job with multiple events");
$ical->SetDates("2013-02-15 01:00", "2013-02-15 02:00");
$ical->SetAlarm();
$ical->SetAlarmText("my first alarm text");
$ical->SetAlarmTrigger(60);
$ical->SetAlarm();
$ical->SetAlarmText("my second alarm text, maybe more urgent");
$ical->SetAlarmTrigger(30);

# finally write the generated ics file to browser or file
$ical->Write(); => output to browser (useful for immediate download)
$ical->Write("myfile.ics"); => output to file
</pre>
