# java-for-object-oriented-solution
Courier Delivery Tracking system
import java.util.*;

class Parcel {
    String trackingId, sender, receiver, status;

    Parcel(String id, String s, String r, String st) {
        trackingId = id;
        sender = s;
        receiver = r;
        status = st;
    }

    void display() {
        System.out.println("\nID: " + trackingId);
        System.out.println("Sender: " + sender);
        System.out.println("Receiver: " + receiver);
        System.out.println("Status: " + status);
    }
}

public class Main {
    static ArrayList<Parcel> list = new ArrayList<>();
    static Scanner sc = new Scanner(System.in);

    public static void main(String[] args) {

        while (true) {
            System.out.println("\n1.Add  2.Track  3.Update  4.View All  5.Exit");
            int ch = sc.nextInt();
            sc.nextLine();

            switch (ch) {
                case 1:
                    System.out.print("Enter ID: ");
                    String id = sc.nextLine();

                    System.out.print("Sender: ");
                    String s = sc.nextLine();

                    System.out.print("Receiver: ");
                    String r = sc.nextLine();

                    list.add(new Parcel(id, s, r, "Dispatched"));
                    System.out.println("Added!");
                    break;

                case 2:
                    System.out.print("Enter ID: ");
                    id = sc.nextLine();

                    boolean found = false;
                    for (Parcel p : list) {
                        if (p.trackingId.equals(id)) {
                            p.display();
                            found = true;
                        }
                    }
                    if (!found) System.out.println("Not found!");
                    break;

                case 3:
                    System.out.print("Enter ID: ");
                    id = sc.nextLine();

                    for (Parcel p : list) {
                        if (p.trackingId.equals(id)) {
                            System.out.print("New Status: ");
                            p.status = sc.nextLine();
                            System.out.println("Updated!");
                        }
                    }
                    break;

                case 4:
                    for (Parcel p : list) {
                        p.display();
                    }
                    break;

                case 5:
                    return;
            }
        }
    }
}
