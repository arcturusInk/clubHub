# clubHub
A web app for student-related information on after school clubs

### Project Overview
ClubHub is a system for student clubs to post information about their events, and for members to join club, post comments, etc.  All users can see public information about clubs and events. Registered users can log in to see and post further information or comments about clubs and events events sponsored by those clubs. Club members may have roles within the clubs that give them additional privileges, i.e.  adding new club members, posting events, adding certain kinds of information, etc.

### Rules of the Database Schema 
Each Person has a unique id, a password, a name, consisting of a first name and a last name, and an e-mail address. 

There are two kinds of People – students and (faculty/staff) advisors.  Advisors have phone numbers and students have gender and class (e.g.  Freshman, sophomore, etc).

Each Club has a unique ID, a name (cname), and a description.  Each club must have at least one advisor.

Clubs may have some keywords to help people find clubs they’d like to join.  People can specify their interests (keywords), to help clubs find people who might want to join them.

Students can belong to clubs.  A student may have some special role(s) within a club, such as president, treasurer, etc.

Clubs can sponsor events.  Each event has a unique ID, a name (ename), a description, a date, a time, and a location, and an indication of whether it is public or just for club members.

People can sign up for events, can post comments about events, and can post comments about clubs. In  some  cases  the  system  may restrict  sign-ups  and/or  comments  to  club  members. People  making comments can designate those comments as being public or just for club members.
