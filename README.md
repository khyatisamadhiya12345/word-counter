# word-counter
Developed a word counter of using java swing and basic java. In this we count the words using string given.
import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

public class WordCounterApp extends JFrame {
    private JTextArea textArea;
    private JLabel wordCountLabel;

    public WordCounterApp() {
        setTitle("Word Counter");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);

        // Initialize components
        textArea = new JTextArea();
        JScrollPane scrollPane = new JScrollPane(textArea);
        JButton countButton = new JButton("Count Words");
        wordCountLabel = new JLabel("Word Count: 0");

        // Set layout
        setLayout(new BoxLayout(getContentPane(), BoxLayout.Y_AXIS));

        // Add components to the frame
        add(scrollPane);
        add(countButton);
(14)
        add(wordCountLabel);

        // Add action listener to the countButton
        countButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                countWords();
            }
        });
    }

    private void countWords() {
        String text = textArea.getText();
        String[] words = text.split("\\s+"); // Split text into words using whitespace as separator
        int wordCount = words.length;
        wordCountLabel.setText("Word Count: " + wordCount);
    }

    public static void main(String[] args) {
        SwingUtilities.invokeLater(new Runnable() {
            @Override
            public void run() {
                WordCounterApp app = new WordCounterApp();
                app.setVisible(true);
            }
        });
    }
}
