# Encapsulation-Practice-MyPlaylist-Song-Class
public class Main {
    public static void main(String[] args) {

        // Create a Song object using the constructor
        Song mySong = new Song("Golden Hour", "JVKE", 209);

        // Use getters to show initial values
        System.out.println("Title: " + mySong.getTitle());
        System.out.println("Duration: " + mySong.getDuration());

        // Update duration using setter (valid update)
        mySong.setDuration(250);
        System.out.println("Updated Duration: " + mySong.getDuration());

        // Attempt to update duration with an invalid value (should be rejected)
        mySong.setDuration(-5);
        System.out.println("Updated Duration (after invalid attempt): " + mySong.getDuration());
    }
}

class Song {

    // Private fields: these values must be hidden from other classes
    private String title;
    private String artist;
    private int durationInSeconds;

    // Constructor: used to create a Song object with initial values
    public Song(String title, String artist, int durationInSeconds) {
        this.title = title;
        this.artist = artist;

        // Use setter so validation applies at creation
        setDuration(durationInSeconds);
    }

    // Getter: allows safe read-only access to the title
    public String getTitle() {
        return title;
    }

    // Getter: allows read-only access to the duration
    public int getDuration() {
        return durationInSeconds;
    }

    // Setter with validation
    public void setDuration(int durationInSeconds) {
        if (durationInSeconds > 0) {
            this.durationInSeconds = durationInSeconds;
        }
        // Invalid values are ignored
    }
}
