import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

class Reservation {
    private String userName;
    private int numberOfSeats;

    public Reservation(String userName, int numberOfSeats) {
        this.userName = userName;
        this.numberOfSeats = numberOfSeats;
    }

    public String getUserName() {
        return userName;
    }

    public int getNumberOfSeats() {
        return numberOfSeats;
    }

    @Override
    public String toString() {
        return "Reservation: User " + userName + ", Seats " + numberOfSeats;
    }
}

public class ReservationSystem {
    private static List<Reservation> reservations = new ArrayList<>();

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Make a reservation");
            System.out.println("2. List all reservations");
            System.out.println("3. Exit");
            System.out.print("Select an option: ");

            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume newline

            switch (choice) {
                case 1:
                    makeReservation(scanner);
                    break;
                case 2:
                    listReservations();
                    break;
                case 3:
                    System.out.println("Exiting...");
                    return;
                default:
                    System.out.println("Invalid choice. Try again.");
                    break;
            }
        }
    }

    private static void makeReservation(Scanner scanner) {
        System.out.print("Enter your name: ");
        String userName = scanner.nextLine();

        System.out.print("Enter the number of seats to reserve: ");
        int numberOfSeats = scanner.nextInt();

        Reservation reservation = new Reservation(userName, numberOfSeats);
        reservations.add(reservation);

        System.out.println("Reservation successful!");
    }

    private static void listReservations() {
        System.out.println("List of Reservations:");
        for (Reservation reservation : reservations) {
            System.out.println(reservation);
        }
    }
}