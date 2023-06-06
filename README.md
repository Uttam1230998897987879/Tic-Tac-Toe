                                                         PROJECT SYNOPSIS                                  


##INTRODUCTION: -

The Tic-tac-toe game is a classic and popular game that is widely enjoyed by people of all ages. The objective of this project is to develop a digital implementation of the Tic-tac-toe game using Java Swing. Java Swing is a powerful framework for creating graphical user interfaces (GUIs) in Java, which provides a rich set of components and tools for building interactive applications.


##OBJECTIVE: -

The main objective of this project is to create a user-friendly and visually appealing version of the Tic-tac-toe game. The game will be designed to allow two players to compete against each other on a 3x3 grid. The players will take turns marking their symbols (X or O) on the grid until one player wins or the game ends in a draw. The project aims to provide an engaging and enjoyable gaming experience to users while showcasing the capabilities of Java Swing for GUI development.


#TECHNOLOGY USED: -

The project will be developed using Java programming language and the Java Swing framework. Java Swing provides a wide range of components, such as buttons, labels, and panels, that can be used to create the game interface. It also offers event handling mechanisms to capture user actions and update the game state accordingly




#SYSTEM REQUIREMENTS: -

The system requirements section explains the necessary conditions for running the project. It states that a system with the Java Development Kit (JDK) installed is required, along with sufficient resources such as memory and processing power. It also mentions that the project will be developed using Java version 8 or higher.
Operating System: - Windows 7/8/10/11 or macOS and LINUX
Processor: - intel core i3 or equivalent
Memory: -4GB or higher



#LIMITATIONS: -

The limitations section outlines the constraints or shortcomings of the project. It mentions that the game does not support advanced features such as playing against a computer AI and is limited to two-player mode. It also specifies that the game is designed for a 3x3 grid and lacks support for larger grid sizes. Additionally, it states that the project does not include online multiplayer capabilities and can only be played on a single device.


#CONCLUSION: - 
The conclusions section provides a summary and final thoughts on the project. It emphasizes that the Tic-tac-toe game project using Java Swing offers an interactive and visually appealing implementation of the game. It highlights the project's potential for showcasing Java Swing's capabilities and the simplicity and versatility of the Java programming language. It acknowledges the project's limitations but emphasizes its value as a learning resource for GUI development and game programming in Java. Lastly, it mentions the user-friendly interface and engaging gameplay as factors that contribute to an enjoyable experience for players.

#CODE for main.java

public class Main {
    public static void main(String[] args) {
       // System.out.println("uttam");
        TicTacToe ticTacToe = new TicTacToe();
    }
}

#CODE for TicTacToe.java

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.Random;

public class TicTacToe implements ActionListener {
    Random random = new Random();
    JFrame frame = new JFrame();
    JPanel title_panel = new JPanel();
    JPanel button_panel = new JPanel();
    JLabel textfield = new JLabel();
    JButton[] button = new JButton[9];
    boolean player1_turn;

    TicTacToe(){

        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(800,800);
        frame.getContentPane().setBackground(new Color(50,50,50));
        frame.setLayout(new BorderLayout());
        frame.setVisible(true);

        textfield.setBackground(new Color(25,25,25));
        textfield.setForeground(new Color(25,255,0));
        textfield.setFont(new Font("Ink Free",Font.BOLD,75));
        textfield.setHorizontalAlignment(JLabel.CENTER);
        textfield.setText("Tic-Tac-Toe");
        textfield.setOpaque(true);

        title_panel.setLayout(new BorderLayout());
        title_panel.setBounds(0,0,800,100);


        button_panel.setLayout(new GridLayout(3,3));
        button_panel.setBackground(new Color(150,150,150));


      for( int i = 0 ; i<9 ; i++){
          button[i] = new JButton();
          button_panel.add(button[i]);
          button[i].setFont(new Font("MV Boli",Font.BOLD,120));
          button[i].setFocusable(false);
          button[i].addActionListener(this);
      }


        title_panel.add(textfield);
        frame.add(title_panel,BorderLayout.NORTH);
        frame.add(button_panel);


        firstTurn();

    }
    @Override
    public void actionPerformed(ActionEvent e){

        for(int i = 0; i<9 ; i++) {
            if(e.getSource()==button[i]) {
                if(player1_turn){
                    if(button[i].getText()==""){
                        button[i].setForeground(new Color(0,0,255));
                        button[i].setText("X");
                        player1_turn= false;
                        textfield.setText("O turn");
                        check();
                    }
                }
                else{
                    if(button[i].getText()==""){
                        button[i].setForeground(new Color(255,0,0));
                        button[i].setText("O");
                        player1_turn= true;
                        textfield.setText("X turn");
                        check();
                    }
                }
            }
        }

    }
    public void firstTurn(){

        try {
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        if(random.nextInt(2)==0) {
          player1_turn= true;
          textfield.setText("x turn");
      }
      else {
          player1_turn= false;
          textfield.setText("O turn");
      }
    }
    public void check(){
        // check X win conditions
           if(
                   (button[0].getText()=="X") &&
                   (button[1].getText()=="X") &&
                           (button[2].getText()=="X")
                   ){
               xWins(0,1,2);
           }
        // check O win conditions
        if(
                (button[3].getText()=="X") &&
                        (button[4].getText()=="X") &&
                        (button[5].getText()=="X")
        ){
            xWins(3,4,5);
        }
        if(
                (button[6].getText()=="X") &&
                        (button[7].getText()=="X") &&
                        (button[8].getText()=="X")
        ){
            xWins(6,7,8);
        }
        if(
                (button[0].getText()=="X") &&
                        (button[3].getText()=="X") &&
                        (button[6].getText()=="X")
        ){
            xWins(0,3,6);
        }
        if(
                (button[1].getText()=="X") &&
                        (button[4].getText()=="X") &&
                        (button[7].getText()=="X")
        ){
            xWins(1,4,7);
        }
        if(
                (button[2].getText()=="X") &&
                        (button[5].getText()=="X") &&
                        (button[8].getText()=="X")
        ){
            xWins(2,5,8);
        }
        if(
                (button[0].getText()=="X") &&
                        (button[4].getText()=="X") &&
                        (button[8].getText()=="X")
        ){
            xWins(0,4,8);
        }
        if(
                (button[2].getText()=="X") &&
                        (button[4].getText()=="X") &&
                        (button[6].getText()=="X")
        ){
            xWins(2,4,6);
        }
        // check O win conditions
        if(
                (button[3].getText()=="O") &&
                        (button[4].getText()=="O") &&
                        (button[5].getText()=="O")
        ){
            oWins(3,4,5);
        }
        if(
                (button[6].getText()=="O") &&
                        (button[7].getText()=="O") &&
                        (button[8].getText()=="O")
        ){
            oWins(6,7,8);
        }
        if(
                (button[0].getText()=="O") &&
                        (button[3].getText()=="O") &&
                        (button[6].getText()=="O")
        ){
            oWins(0,3,6);
        }
        if(
                (button[1].getText()=="O") &&
                        (button[4].getText()=="O") &&
                        (button[7].getText()=="O")
        ){
            oWins(1,4,7);
        }
        if(
                (button[2].getText()=="O") &&
                        (button[5].getText()=="O") &&
                        (button[8].getText()=="O")
        ){
            oWins(2,5,8);
        }
        if(
                (button[0].getText()=="O") &&
                        (button[4].getText()=="O") &&
                        (button[8].getText()=="O")
        ){
            oWins(0,4,8);
        }
        if(
                (button[2].getText()=="O") &&
                        (button[4].getText()=="O") &&
                        (button[6].getText()=="O")
        ){
            oWins(2,4,6);
        }
    }
    public void xWins(int a,int b,int c){
     button[a].setBackground(Color.GREEN);
     button[b].setBackground(Color.GREEN);
     button[c].setBackground(Color.GREEN);
     for(int i = 0 ; i<9 ; i++) {
         button[i].setEnabled(false);
     }
     textfield.setText("X wins");
    }
    public void oWins(int a,int b,int c){
     button[a].setBackground(Color.GREEN);
     button[b].setBackground(Color.GREEN);
     button[c].setBackground(Color.GREEN);
     for(int i = 0 ; i< 9; i++){
         button[i].setEnabled(true);
     }
     textfield.setText("O wins");
    }
}
