# Booking
Booking System Project
Overview
This project is a Booking System that demonstrates the use of various design patterns within an MVC (Model-View-Controller) architecture. The system includes functionalities to manage different types of bookings (e.g., hotel, flight, car rentals) and extends features such as add-ons, notifications, and a simplified booking workflow.

Architecture Pattern: MVC (Model-View-Controller)
Justification: MVC is selected as it allows a clear separation of responsibilities:

Model: Manages data and business logic (e.g., booking details).
View: Displays data to the user.
Controller: Handles user input, processes it, and updates the model and view accordingly.
Design Patterns Used
This project demonstrates the use of multiple design patterns, classified into creational, structural, and behavioral categories:

1. Creational Patterns
Singleton Pattern
Purpose: Ensures only one instance of a resource-intensive object, like a database connection.
Implementation:
java

public class DatabaseConnection {
    private static DatabaseConnection instance;

    private DatabaseConnection() {}

    public static DatabaseConnection getInstance() {
        if (instance == null) {
            instance = new DatabaseConnection();
        }
        return instance;
    }
}
Factory Method Pattern
Purpose: Allows the creation of different booking types (e.g., Hotel, Flight, CarRental) through a factory interface without modifying existing code.
Implementation:
java

abstract class Booking { /*...*/ }

class BookingFactory {
    public static Booking createBooking(String type) {
        switch (type) {
            case "hotel": return new HotelBooking();
            case "flight": return new FlightBooking();
            case "car": return new CarRentalBooking();
            default: throw new IllegalArgumentException("Unknown booking type");
        }
    }
}
2. Structural Patterns
Facade Pattern
Purpose: Simplifies interactions with multiple subsystems (Availability, Payment, Notification) to provide a simple interface for making bookings.
Implementation:
java

class BookingFacade {
    public void book(String bookingType, double amount) { /*...*/ }
}
Decorator Pattern
Purpose: Allows dynamic addition of features (e.g., breakfast, insurance) to a booking without changing the core booking class.
Implementation:
java

interface BookingDecorator { /*...*/ }

class BreakfastAddon extends BasicBooking { /*...*/ }
3. Behavioral Patterns
Observer Pattern
Purpose: Notifies users when there are changes, such as booking confirmations or availability updates.
Implementation:
java

interface Observer { /*...*/ }

class BookingNotifier { /*...*/ }
Command Pattern
Purpose: Manages actions like booking and cancelling, allowing new commands to be added flexibly.
Implementation:
java

interface Command { /*...*/ }

class BookCommand implements Command { /*...*/ }
Class Diagrams and UML
Note: Diagrams can be generated using tools like UMLet, Lucidchart, or StarUML.

Class Diagram: Shows the structure of the project with class relationships for Model, View, Controller, and key design patterns.
Sequence Diagram: Demonstrates interaction flow in key functionalities, such as creating a booking, applying add-ons, and sending notifications.
How to Run the Project
Prerequisites
Java Development Kit (JDK): Ensure you have JDK installed (version 8+).
IDE (Optional): Use an IDE like IntelliJ IDEA or Eclipse for easy code navigation and execution.
Steps
Clone the repository:


git clone <repository_url>
Navigate to the project directory.
Compile the code:


javac *.java
Run the main class:

Копировать код
java Main
Sample Usage
Initialize Database:
Uses Singleton pattern to ensure a single database connection.


DatabaseConnection connection = DatabaseConnection.getInstance();
connection.connect();
Create Bookings:
Uses Factory Method to create different booking types.


Booking booking = BookingFactory.createBooking("hotel");
booking.book();
Apply Add-ons:
Uses Decorator pattern for adding features like breakfast or insurance to a booking.

BookingDecorator bookingWithBreakfast = new BreakfastAddon(new BasicBooking());
Booking Notifications:
Uses Observer to notify users of booking status.

BookingNotifier notifier = new BookingNotifier();
notifier.notifyAvailability("hotel");

duction-ready application.
