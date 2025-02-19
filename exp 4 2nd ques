import java.util.*;

class TicketBookingSystem {
    private final int totalSeats = 5; 
    private final boolean[] seats = new boolean[totalSeats];

    public synchronized boolean bookSeat(int seatNumber, String user) {
        if (seatNumber < 0 || seatNumber >= totalSeats) {
            System.out.println(user + " tried booking an invalid seat.");
            return false;
        }
        if (!seats[seatNumber]) {
            seats[seatNumber] = true;
            System.out.println(user + " successfully booked seat " + seatNumber);
            return true;
        } else {
            System.out.println(user + " tried to book seat " + seatNumber + ", but it's already booked.");
            return false;
        }
    }
}

class BookingThread extends Thread {
    private final TicketBookingSystem system;
    private final String user;
    private final int seatNumber;

    public BookingThread(TicketBookingSystem system, String user, int seatNumber, int priority) {
        this.system = system;
        this.user = user;
        this.seatNumber = seatNumber;
        setPriority(priority);
    }

    @Override
    public void run() {
        system.bookSeat(seatNumber, user);
    }
}

public class TicketBookingApp {
    public static void main(String[] args) {
        TicketBookingSystem system = new TicketBookingSystem();

        List<BookingThread> threads = new ArrayList<>();
        
        threads.add(new BookingThread(system, "VIP_John", 2, Thread.MAX_PRIORITY));
        threads.add(new BookingThread(system, "Regular_Alice", 2, Thread.NORM_PRIORITY));
        threads.add(new BookingThread(system, "VIP_Mary", 3, Thread.MAX_PRIORITY));
        threads.add(new BookingThread(system, "Regular_Bob", 3, Thread.NORM_PRIORITY));
        threads.add(new BookingThread(system, "VIP_Steve", 1, Thread.MAX_PRIORITY));
        threads.add(new BookingThread(system, "Regular_Charlie", 1, Thread.NORM_PRIORITY));

        Collections.shuffle(threads);

        for (BookingThread thread : threads) {
            thread.start();
        }

        for (BookingThread thread : threads) {
            try {
                thread.join();
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
        }

        System.out.println("Booking process completed.");
    }
}
