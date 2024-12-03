# Intro-to-computer-networks

import java.io.*;
import java.net.*;

public class Client {
    public static void main(String[] args) {
        try {
            // Connect to the server
            Socket socket = new Socket("localhost", 12345);

            // Streams created for sending and receiving data
            DataOutputStream output = new DataOutputStream(socket.getOutputStream());
            DataInputStream input = new DataInputStream(socket.getInputStream());

            // Send the radius to the server
            double radius = 5.0; 
            System.out.println("Sending radius to server: " + radius);
            output.writeDouble(radius);
            output.flush();

            // Receive the area from the server
            double area = input.readDouble();
            System.out.println("Received area from server: " + area);

            // Close streams and socket
            input.close();
            output.close();
            socket.close();
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}

