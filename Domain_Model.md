# Domain Model Περιγραφή
---
#### Company : Οντότητα που περιλαμβάνει την εταιρία περιέχει ως μεταβλητές το όνομα (name), το τηλέφωνο (phone),το ΑΦΜ (afm)
#### Customer : Οντότητα που περιλαμβάνει τους πελάτες της εταιρίας έχει τις μεταβλήτες όνομα (name), διεύθυνση (address), τηλέφωνο (phone) και ο πελάτης μπορεί να κατέχει (has) απο 0 έως άπειρα οχήματα (Vehicle) και χαραχτηρίζεται από την μεταβλητή id
#### Vehicle : Οντότητα που περιλαμβάνει τα οχήματα με τις μεταβλητές πινακίδα (licence plate) , μοντέλο (model name) , χιλιόμετρα (kms) , αριθμός πλαισίου (vehicle identification number) , χρώμα (color) και χαρακτηρίζεται από την μεταβλητή id και μπορεί να υποβληθεί (gets) απο 0 εώς άπειρες εργασίες (operations)
#### Operation : Οντότητα που περιλαμβάνει τις εργασίες με τις μεταβλητές κόστος (cost), περιγραφή (description) , καθυστέρηση (delay) , ημερομηνία (date) και χαρακτηρίζεται απο το id και είναι η εργασία που γίνεται σε ένα όχημα με id = carId το Operation μπορεί να είναι είτε Repair είτε Service.
#### Repair: Περίπτωση operation περιγράφει την επισκευή ενός οχήματος έχεις τις μεταβλητές ανταλλακτικά (parts) , ώρες εργασίας (hours)
#### Service: Περίπτωση operation περιγράφει το σερβις ενός οχήματος έχει τις μεταβλητές πληροφορίες (info) , ώρες εργασίας (hours)
#### Appointment: Οντότητα που περιγράφει ένα ραντεβού με έναν πελάτη με id = customerId που πιθανώς μπορεί να είναι για κάποια εργασία με id = operationId. Έχει τις μεταβλητές ημερομηνία (date) και διάρκεια (length)
#### Agenda: Οντότητα που περιγράφη το ημερολόγιο της εταιρίας και περιέχει όλα τα ραντεβού (agenda) και έχει τις μεταβλητές ώρες εργασίας (working hours) και ώρες αχμής (busy hours)
#### State: Είναι η κατάσταση που βρίσκεται κάθε εργασία (operation) με id = operationId και έχει τις μεταβλητές αναμενόμενος χρόνος (estimated time), περιγραφή (description) και πρόοδος (progress). Κάθε κατάσταση αντιστοιχεί σε μια μοναδική εργασία
#### Campaign: Είναι η περίπτωση που θέλουμε να ενημερώσουμε τους χρήστες με ένα notification με συγκεκριμένο type σε συγκεκριμένους χρήστες.

# Methods: 
---
#### Campaign Methods : sendCampaign() στέλνει το notificationText με συγκεκριμένο notificationType σε όλους τους χρήστες που βρίσκονται στο customersList.
#### changeTime() αλλάζει το deliveryTime δηλαδή την ώρα που θα παραδωθεί το Notification στους χρήστες(customers)
#### Company Methods: getName(),getAfm(),getAddress() επιστρέφει τα συγκεκρίμενα attributes από το Company, getDirections() επιστρέφει ένα link με την τοποθεσία του καταστήματος στο Google Maps, getAllCustomers() επιστρέφει όλους τους πελάτες από την εταιρία. 
#### Customer Methods: changeName() αλλάζει το όνομα του πελάτη , addCar() προσθέτει αυτοκίνητο στον customer.
#### Agenda Methods: getCalendar() επιστρέφει όλα τα προγραμματισμένα ραντεβού(Appointment), updateBusyHours() ανανεώνει τα BusyHours.
#### Appointment Methods: changeDate() αλλάζει την ημερομηνία ενός Appointment, updateAgenda() περνάει τα ραντεβού στην Agenda, getAppointment() επιστρέφει τα δεδομένα του Appointment.
#### Operation Methods: getDelay(),getDescription(),getCost(),getType(),getCarDetails() επιστρέφει τις αντίστοιχες μεταβλητές
#### State Methods: getProgress(),getDescription() επιστρέφει τις αντίστοιχες μεταβλητές.
#### Vehicle Methods: getHistory() επιστρέφει το τελευταίο operation του vehicle , getCarDetails() επιστρέφει όλα τα δεδομένα για το Vehicle, createQR() δημιουργεί QR code για το id του Vehicle, getService() επιστρέφει την ημερομηνία και τα δεδομένα του τελευταίου σέρβις.
# Screens: 
---
#### Main Screen : displayLastService() επιστρέφει την οθόνη με τα δεδόμενα του τελευταίου service , displayScedule() επιστρέφει την οθόνη με το Schedule
#### Progress Details: displayProgress() επιστρέφει τα δεδόμενα απο το State του Operation , refreshUI() ανανεώνει με τα καινούργια δεδομένα απο το state, displayFullInfo() επιστρέφει την οθόνη με όλες τις πληροφορίες απο ένα Operation , displayContact() εμφανίζει την οθόνη με τις πληροφορίες του Company.
#### History Screen: displayInfo(download) Επιστρέφει την οθόνη με το ιστορίκο του Vehicle με την επιλογή του download
#### Contact Us: display(call) εμφανίζει την οθόνη με τις πληροφορίες με την επιλογή του call(), getInfo() παίρνει τα δεδόμενα απο το Company
#### Schedule Now: checkTime() τσεκάρει αν υπάρχει διαθέσιμη ώρα για Appointment, displaySchedule() εμφανίζει τα δεδόμενα του Appointment που δημιουργήθηκε.
![image](https://user-images.githubusercontent.com/51947061/169593434-bf81aaa7-25b0-4dbe-804b-03b6a9561de3.png)
