# Functional Requirements

## Ticket systems

## Motivation

The Student Sphere MVP answer issues related with association life at EPFL:

- Visibility of events and associations
- Recruitment
- Event ticketing
- Event Staffing
- Centralisation of Association information

These activities as an Association at EPFL is typically resolved by an intense and tiresome communication campaign through Instagram and Physical posters. Both not having as sole purpose to reunite students with same goals and interests. The key to our concept is centralisation of information. We want to create a place for each Association can manage their identity and management. In Association life at EPFL association mangers are also users that want to attend events and recurrent issue is the physical ticket system that is vulnerable to falsification and loss. We aim at changing the way we carry and use our tickets

### Proposed Solution

A wallet system on the application that allows users get tickets with a QR code or NFC scanner. Staffs have staff tickets created as soon as they are accepted as staffs allowing a smoother management of tickets and a faster count how many people have tickets as staff or ass participants. The tickets are stored in general collection "tickets" where all tickets are stored with their attributes. The user on the other hand has the ticket ID he owns in a collection of his own so it is easier to fetch the tickets in firebase read calls. Tickets can now also be created by scanning a QRcode associated with the event.

## User identification (Scrapping)

### Motivation

We need at every login know who is the user for the EPFL community and double check information. At EPFL everyone is known with their sciper and being able to link accounts with it and therefore in a near future automatise admin tasks for registration and statistics on users.

### Proposed Solution

At every Signup we call a firebase function that scraps with users email its sciper, section, name , surname and possible roles in associations (very hard as EPFL's website does not use the same acronym as the association list website). The firebase function creates an element User with its arguments and stores it in the collection "users", if the email is not found it creates an empty user and is considered and out of EPFL user however many associations welcome members from other schools so we don't want to limit accessibility.

## Inaccessible information

### Motivation

Every semester we are bombarded by emails for recruitment for events and associations and on other platforms like instagram. Our will is to centralise this information not only during the beginning of the semester but also all along so people could go back and check availabilities of positions or tickets for events.

### Proposed Solution

Each Association has its own page that they can manage, for this we have  3 types of elements, events, news and open positions that can modified and customised to the association's need. Event item can have staffs and create tickets, open positions can allow users to join associations and news item can inform students on updates or in a near future trigger notifications. They can be modified with images and descriptions. The organisation of the page is made so the user has as much freedom without making it a tedious task.

##  Architectural Diagram

cf. Appendix 1

