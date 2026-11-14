# Week 11-12 Assignment 2/4
```java
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JTextField;

public class SalaryCalculator extends JFrame implements ActionListener {
    private JLabel wageLabel;
    private JLabel salLabel;
    private JTextField salField;
    private JTextField wageField;
    private JButton calcButton;
    private JButton resetButton;

    public SalaryCalculator() {
        GridBagConstraints positionConst;

        setTitle("Salary");

        wageLabel = new JLabel("Hourly wage:");
        salLabel = new JLabel("Yearly salary:");

        wageField = new JTextField(15);
        wageField.setEditable(true);
        wageField.setText("");

        salField = new JTextField(15);
        salField.setEditable(false);
        salField.setText("");

        calcButton = new JButton("Calculate");
        resetButton = new JButton("Reset");

        calcButton.addActionListener(this);

        resetButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent event) {
                wageField.setText("");
                salField.setText("");
            }
        });

        setLayout(new GridBagLayout());
        positionConst = new GridBagConstraints();
        positionConst.insets = new Insets(10, 10, 10, 10);

        positionConst.gridx = 0;
        positionConst.gridy = 0;
        add(wageLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 0;
        add(wageField, positionConst);

        positionConst.gridx = 0;
        positionConst.gridy = 1;
        add(salLabel, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 1;
        add(salField, positionConst);

        positionConst.gridx = 0;
        positionConst.gridy = 2;
        add(calcButton, positionConst);

        positionConst.gridx = 1;
        positionConst.gridy = 2;
        add(resetButton, positionConst);
    }

    @Override
    public void actionPerformed(ActionEvent event) {
        String userInput = wageField.getText();

        try {
            double hourlyWage = Double.parseDouble(userInput);

            if (hourlyWage < 0) {
                JOptionPane.showMessageDialog(this,
                        "Hourly wage cannot be negative.",
                        "Input Error",
                        JOptionPane.ERROR_MESSAGE);
                return;
            }

            double yearlySalary = hourlyWage * 40 * 50;
            salField.setText(String.format("%.2f", yearlySalary));

        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this,
                    "Please enter a valid number for the hourly wage.",
                    "Input Error",
                    JOptionPane.ERROR_MESSAGE);
        }
    }

    public static void main(String[] args) {
        SalaryCalculator myFrame = new SalaryCalculator();

        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```
