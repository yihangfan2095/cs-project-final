# cs-project-final
import processing.core.*;

import java.util.Timer;
import java.util.TimerTask;


public class JavJavBeans extends PApplet {
    
//    private class time extends TimerTask{
//   	 public void run() {
//   	    	System.out.println("Hello World!");
//   	 	}
//   	 
//   	 
//    }
    
    
    static int maxHappiness = 50;
    static int maxFood = 50;
    static int maxEnergy = 50;
    
    
    static int happiness = 50;
    static int food = 50;
    static int energy = 50;
    static int age = 0;
    static int money = 50;
    static int stage = 0;
    
    static boolean overButton = false;
    static int whichButton = 1;
    
    static int buttonsSize = 60;
    static int buttonsPositionX = 20;
    static int buttonsSeparation = 15;
    static int miniGameButtonY = 160;

    static int feedButtonY = miniGameButtonY + buttonsSize + buttonsSeparation;
    static int sleepButtonY = miniGameButtonY + 2*buttonsSize + 2*buttonsSeparation;
    
    public JavJavBeans(){}

//    public static void main(String[] args) {
//   	 // TODO Auto-generated method stub
//   	 Timer time = new Timer();
//   	 time.schedule(new JavJavBeans(), 0, 5000);
//   	 
//   	 PApplet.main("JavJavBeans");
//    }
    
    public void settings(){
   	 size(400, 400);
    }

    public void setup(){
   	 background(255);
    }
    
    public void draw() {
   	 square(buttonsPositionX, miniGameButtonY, buttonsSize);
   	 square(buttonsPositionX, feedButtonY, buttonsSize);
   	 square(buttonsPositionX, sleepButtonY, buttonsSize);
   	 // Test if the cursor is over the box
   	 checkOverBox();
    }
    
    public void checkOverBox() {
   	 if (mouseX > buttonsPositionX && mouseX < buttonsPositionX+buttonsSize && mouseY > miniGameButtonY && mouseY < miniGameButtonY+buttonsSize) {
   		 overButton = true;
   		 whichButton = 1;
   	 } else if(mouseX > buttonsPositionX && mouseX < buttonsPositionX+buttonsSize && mouseY > feedButtonY && mouseY < feedButtonY+buttonsSize) {
   		 overButton = true;
   		 whichButton = 2;
   	 } else if(mouseX > buttonsPositionX && mouseX < buttonsPositionX+buttonsSize && mouseY > sleepButtonY && mouseY < sleepButtonY+buttonsSize) {
   		 overButton = true;
   		 whichButton = 3;
   	 } else {
   		 overButton = false;
   	 }
    }

    public static void animal(){
   	 
    }

    public static void feed(){
   	 if(money >= 5) {
   		 //System.out.println("test");
   		 money -= 5;
   		 food += 10;
   		 if(food > maxFood)
   			 food = maxFood;
   		 
   		 if(energy < maxEnergy / 2) {
   			 energy += 5;
   			 if(energy > maxEnergy / 2)
   				 energy = maxEnergy / 2;
   		 }
   	 } else {
   		 //NOTIFY YOU HAVE NOT ENOUGH MONEY!!
   	 }
    }

    //need time
    public static void sleep(){
   	 
    }

    //pass a random difficulty value, more difficult = more money
    public static void miniGame() {
   	 if(energy >= 10) {
   		 //MINIGAME STUFF
   		 energy -= 10;
   		 decreaseFood(5);
   		 money += 10; //pass money() function that gives more money depending on minigame difficulty.
   	 }
   	 
   	 
    }
    
    //pet animal (increase happiness by x, decrease energy and food by 1
    public static void pet(){
   	 
    }

    public static void decreaseFood(int amount){
   	 food -= amount;
    }

    //need minigame
    public static void money(){

    }

    //need time
    public static void happiness(){

    }

    //need time
    public static void energy(){

    }
    
    //need time
    public static void increaseAge(){
   	 
    }
    
    // DELETE THIS LATER!!!!!
    public static void printStuff(){
   	 System.out.println("Happines: "+happiness);
   	 System.out.println("Food: "+food);
   	 System.out.println("Energy: "+energy);
   	 System.out.println("Age: "+age);
   	 System.out.println("Money: "+money);
    }
    
    public static void execute(){
   	 //printStuff();
   	 Timer time = new Timer();
   	 time.schedule(new PlayGame(), 0, 5000);
   	 PApplet.main("JavJavBeans");
    }
    
    public void mouseClicked() {
   	 if(overButton) {
   		 switch(whichButton) {
   		 case 1:
   			 //MINIGAME STUFF
   			 miniGame();
   			 printStuff();
   			 break;
   		 case 2:
   			 //FEED (Check if you have money)
   			 feed();
   			 printStuff();
   			 fill(70);
   			 break;
   		 case 3:
   			 //SLEEP STUFF
   			 break;
   		 }
   	 }
    }

}
