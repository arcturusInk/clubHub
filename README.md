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

### The Features ClubHub Supports
1. View Public Info: All users, whether logged in or not, can
- view list of topics
- select a topic and see list of clubs (cname, desc) that are about that topic
- see list of public events occurring in the coming day

2. Login: User enters pid, x and password y via forms on login page.  This data is sent as POST parameters to the login-authentication component, which checks whether there is a tuple in the Person table with pid = x and the passwd = md5(y)
- If so, login is successful.  A session is initiated with pid stored as a session variables.  Option-ally, store other session variables.  Control is redirected to a component that displays the user’s home page.
- If not, login is unsuccessful.  A message is displayed indicating this to the user.
![1&2](https://user-images.githubusercontent.com/9923181/48306676-b4c45700-e50a-11e8-92c7-64d195e88574.JPG)

3. Display Home Page: Once a user has logged in, ClubHub will display her home page.  Also, after other actions or sequences of related actions, are executed, control will return to component that displays the home page.  The home page should display
- Error message if the previous action was not successful,
- Some mechanism for the user to choose the use case she wants to execute.  You may choose to provide links to other URLS that will present the interfaces for other use cases, or you may include those interfaces directly on the home page. 
- Any other information you’d like to include.  For example, you might want to include clubs the user belongs to, events she’s signed up for, etc on the home page, or you may prefer to just show them when she does some of the following use cases.

After logging in successfully a user may do any of the following use cases:

4. View My Events:  Provide various ways for the user to see upcoming events of interest.  These can be included as a single use case or as separate use cases.  The default should be showing events for the current day and the next three days.  Optionally you may include a way for the user to specify a range of dates.  In each case, the display should include the ename, date, time, location, and name of sponsoring club.
- upcoming events for which this user has signed up
- upcoming events that are public or are sponsored by clubs to which this user belongs
![4](https://user-images.githubusercontent.com/9923181/48306683-e3423200-e50a-11e8-8e60-6cc077268895.JPG)

5. Sign up for an event: User chooses an event that they are eligible for (because they belong to the sponsoring club or because it’s public) and signs up for the event. If the user has previously signed up for the event no additional action is needed (but ClubHub should not crash)
![5](https://user-images.githubusercontent.com/9923181/48306686-ea694000-e50a-11e8-95c9-ed1f9331fdae.JPG)

6. Post a new event: User enters ename, date, time, description, location, sponsoring club, and indication of whether event is public.
ClubHub records the event with a new eid and notes the sponsoring club. The user must be a member of the club with role “admin” to post an event! If not, ClubHub displays a meaningful error message.
![6](https://user-images.githubusercontent.com/9923181/48306681-cefe3500-e50a-11e8-869d-2eb870080153.JPG)

7. Check club’s events : For  each  club  for  which  the  user  has  ”admin”  role, ClubHub displays upcoming events (eid, ename, sponsoring clubs) and the number of people who have have signed up for each. Use an outer join to include events for which no one has signed up.

8. Logout: The session is destroyed and a “goodbye” page or the login page is displayed.
