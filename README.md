# java-for-object-oriented-solution
Courier Delivery Tracking system
import java.util.ArrayList;
import java.util.Scanner;

class Parcel {
    private String parcelId;
    private String status;

    public Parcel(String parcelId) {
        this.parcelId = parcelId;
        this.status = "Dispatched";
    }

    public String getParcelId() {
        return parcelId;
    }

    public String getStatus() {
        return status;
    }

    public void updateStatus(String newStatus) {
        status = newStatus;
    }

    public void displayDetails() {
        System.out.println("Parcel ID: " + parcelId);
        System.out.println("Status: " + status);
    }
}

public class CourierSystem {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);
        ArrayList<Parcel> parcels = new ArrayList<>();

        parcels.add(new Parcel("P101"));
        parcels.add(new Parcel("P102"));
        parcels.add(new Parcel("P103"));

        parcels.get(0).updateStatus("In Transit");
        parcels.get(1).updateStatus("Delivered");

        while (true) {

            System.out.println("\n===== Courier Delivery Tracking System =====");
            System.out.println("1. Add Parcel");
            System.out.println("2. Track Parcel");
            System.out.println("3. Update Status");
            System.out.println("4. View All Parcels");
            System.out.println("5. Exit");
            System.out.print("Enter Choice: ");

            int choice = sc.nextInt();
            sc.nextLine();

            switch (choice) {

                case 1:
                    System.out.print("Enter Parcel ID: ");
                    String id = sc.nextLine();

                    parcels.add(new Parcel(id));
                    System.out.println("Parcel Added Successfully!");
                    break;

                case 2:
                    System.out.print("Enter Parcel ID: ");
                    id = sc.nextLine();

                    boolean found = false;

                    for (Parcel p : parcels) {
                        if (p.getParcelId().equalsIgnoreCase(id)) {
                            System.out.println("Status: " + p.getStatus());
                            found = true;
                            break;
                        }
                    }

                    if (!found) {
                        System.out.println("Parcel Not Found!");
                    }
                    break;

                case 3:
                    System.out.print("Enter Parcel ID: ");
                    id = sc.nextLine();

                    found = false;

                    for (Parcel p : parcels) {
                        if (p.getParcelId().equalsIgnoreCase(id)) {

                            System.out.println("1. Dispatched");
                            System.out.println("2. In Transit");
                            System.out.println("3. Out for Delivery");
                            System.out.println("4. Delivered");

                            System.out.print("Select Status: ");
                            int statusChoice = sc.nextInt();
                            sc.nextLine();

                            switch (statusChoice) {
                                case 1:
                                    p.updateStatus("Dispatched");
                                    break;
                                case 2:
                                    p.updateStatus("In Transit");
                                    break;
                                case 3:
                                    p.updateStatus("Out for Delivery");
                                    break;
                                case 4:
                                    p.updateStatus("Delivered");
                                    break;
                                default:
                                    System.out.println("Invalid Status!");
                            }

                            System.out.println("Status Updated Successfully!");
                            found = true;
                            break;
                        }
                    }

                    if (!found) {
                        System.out.println("Parcel Not Found!");
                    }
                    break;

                case 4:
                    System.out.println("\nAll Parcels:");
                    for (Parcel p : parcels) {
                        p.displayDetails();
                        System.out.println("------------------");
                    }
                    break;

                case 5:
                    System.out.println("Thank You!");
                    sc.close();
                    System.exit(0);

                default:
                    System.out.println("Invalid Choice!");
            }
        }
    }
}

