# Encapsulation-Practice-MyPlaylist-Song-Class
public class Main {
    public static void main(String[] args) {

        // Create a Song object
        Song mySong = new Song("Golden Hour", "JVKE", 209);

        // Display initial values
        System.out.println(mySong);

        // Valid update
        mySong.setDuration(250);
        System.out.println("After valid update:");
        System.out.println(mySong);

        // Invalid update (should be rejected safely)
        mySong.setDuration(-5);
        System.out.println("After invalid update attempt:");
        System.out.println(mySong);
    }
}

class Song {

    // Constants improve readability and reusability
    private static final int MAX_DURATION = 600; // 10 minutes

    // Private fields (encapsulation)
    private final String title;
    private final String artist;
    private int durationInSeconds;

    // Constructor with validation
    public Song(String title, String artist, int durationInSeconds) {
        this.title = title;
        this.artist = artist;
        setDuration(durationInSeconds);
    }

    // Getters (read-only access)
    public String getTitle() {
        return title;
    }

    public String getArtist() {
        return artist;
    }

    public int getDuration() {
        return durationInSeconds;
    }

    // Setter with strong validation and safe rejection
    public void setDuration(int durationInSeconds) {
        if (durationInSeconds > 0 && durationInSeconds <= MAX_DURATION) {
            this.durationInSeconds = durationInSeconds;
        } else {
            // Safe rejection (no crash, no corruption)
            System.out.println(
                "Invalid duration ignored: " + durationInSeconds +
                " (must be between 1 and " + MAX_DURATION + " seconds)"
            );
        }
    }

    // toString improves reuse, debugging, and clean output
    @Override
    public String toString() {
        return "Song Details:\n" +
               "Title: " + title + "\n" +
               "Artist: " + artist + "\n" +
               "Duration: " + durationInSeconds + " seconds\n";
    }
}
