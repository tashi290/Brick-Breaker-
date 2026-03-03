# Brick-Breaker-
A video game made in JavaScript. Made on complier JDK7.0_80 


import java.applet.*;
import java.awt.*;
import java.awt.event.*;
// this applet prints out the key stroke

public class BrickBreaker extends Applet implements KeyListener, Runnable
{
  Font myfont, deadfont, myfont2;
  int blockCounter;
  int yellowX, yellowY, yellowW, yellowH, yellowX2, yellowY2, yellowW2, yellowH2, yellowX3, yellowY3, yellowW3, yellowH3, yellowX4, yellowY4, yellowW4, yellowH4, yellowX5, yellowY5, yellowW5, yellowH5;
  int blueX, blueY, blueW, blueH, blueX2, blueY2, blueW2, blueH2, blueX3, blueY3, blueW3, blueH3, blueX4, blueY4, blueW4, blueH4, blueX5, blueY5, blueW5, blueH5, lvl;
  int greenX, greenY, greenW, greenH, greenX2, greenY2, greenW2, greenH2, greenX3, greenY3, greenW3, greenH3, greenX4, greenY4, greenW4, greenH4, greenX5, greenY5, greenW5, greenH5;
  int appletHeight, appletWidth, ballX, ballY, ballSize, score, landX, landY, lives, landW, landH, ballW, ballH, redW, redH, redX, redY, redW2, redH2, redX2, redY2, redX3, redY3, redW3, redH3, redX4, redY4, redW4, redH4, redX5, redY5, redW5, redH5;
  double ballXS, ballYS, norm;
  Image spaceBG, ball, landingPad, brick1, heart, offscreen, redBlock, blueBlock, greenBlock, yellowBlock;
  final int screenW = 1280, screenH = 970; 
  Graphics bufferGraphics;
  boolean leftKey;
  boolean rightKey;
  private boolean running;
  private boolean gameStarted;
  private boolean spaceClicked;
  private boolean showRed1;
  private boolean showRed2;
  private boolean showRed3;
  private boolean showRed4;
  private boolean showRed5;
  private boolean showBlue;
  private boolean showBlue2;
  private boolean showBlue3;
  private boolean showBlue4;
  private boolean showBlue5;
  private boolean showGreen;
  private boolean showGreen2;
  private boolean showGreen3;
  private boolean showGreen4;
  private boolean showGreen5;
  private boolean showYellow;
  private boolean showYellow2;
  private boolean showYellow3;
  private boolean showYellow4;
  private boolean showYellow5;
  // *****************************************************************
  public void init()
  {
    addKeyListener(this);
    ballX = 500;
    ballY = 770;
    ballSize = 30;
    ballW = 30;
    ballH = 30;
    ballXS= 5; 
    ballYS= 5;
    
    landX = 470;
    landY = 800;
    landW = 200;
    landH = 20;
    
    
// Blocks Red
    redW = 230;
    redH = 30;
    redX = 35;
    redY = 50;
    
    redW2 = 230;
    redH2 = 30;
    redX2 = 275;
    redY2 = 50;
    
    redX3 = 515;
    redY3 = 50;
    redW3 = 230;
    redH3 = 30;
    
    redX4 = 755;
    redY4 = 50;
    redW4 = 230;
    redH4 = 30;
    
    redX5 = 995;
    redY5 = 50;
    redW5 = 230;
    redH5 = 30;

// Blocks Blue
    blueX = 35;
    blueY = 90;
    blueW = 230;
    blueH = 30;
    
    blueX2 = 275;
    blueY2 = 90;
    blueW2 = 230;
    blueH2 = 30;
    
    blueX3 = 515;
    blueY3 = 90;
    blueW3 = 230;
    blueH3 = 30;
    
    blueX4 = 755;
    blueY4 = 90;
    blueW4 = 230;
    blueH4 = 30;
    
    blueX5 = 995;
    blueY5 = 90;
    blueW5 = 230;
    blueH5 = 30;
    
// Blocks Green
    greenX = 35;
    greenY = 130;
    greenW = 230;
    greenH = 30;
    
    greenX2 = 275;
    greenY2 = 130;
    greenW2 = 230;
    greenH2 = 30;
    
    greenX3 = 515;
    greenY3 = 130;
    greenW3 = 230;
    greenH3 = 30;
    
    greenX4 = 755;
    greenY4 = 130;
    greenW4 = 230;
    greenH4 = 30;
    
    greenX5 = 995;
    greenY5 = 130;
    greenW5 = 230;
    greenH5 = 30;
    
// Blocks Yellow
    yellowX = 35;
    yellowY = 170;
    yellowW = 230;
    yellowH = 30;
    
    yellowX2 = 275;
    yellowY2 = 170;
    yellowW2 = 230;
    yellowH2 = 30;
    
    yellowX3 = 515;
    yellowY3 = 170;
    yellowW3 = 230;
    yellowH3 = 30;
    
    yellowX4 = 755;
    yellowY4 = 170;
    yellowW4 = 230;
    yellowH4 = 30;
    
    yellowX5 = 995;
    yellowY5 = 170;
    yellowW5 = 230;
    yellowH5 = 30;
    
    lives = 3;
    lvl = 1;
    score = 0;
    blockCounter = 20;
    
    // show the blocks;
    leftKey = false;
    rightKey = false;
    running = true;
    gameStarted = false;
    spaceClicked = false;
    showRed1 = true;
    showRed2 = true;
    showRed3 = true;
    showRed4 = true;
    showRed5 = true;
    showBlue = true;
    showBlue2 = true;
    showBlue3 = true;
    showBlue4 = true;
    showBlue5 = true;
    showGreen = true;
    showGreen2 = true;
    showGreen3 = true;
    showGreen4 = true;
    showGreen5 = true;
    showYellow = true;
    showYellow2 = true;
    showYellow3 = true;
    showYellow4 = true;
    showYellow5 = true;
    
    
    
    // intialize all images and backround
    redBlock = this.getImage (this.getDocumentBase(), "RedBlock.jpg");
    heart = this.getImage (this.getDocumentBase(), "heartLives.png");
    spaceBG = this.getImage (this.getDocumentBase(), "SpaceBackround.jpg");
    ball = this.getImage (this.getDocumentBase(), "ball.png");
    landingPad = this.getImage (this.getDocumentBase(), "landingPad.png");
    blueBlock = this.getImage (this.getDocumentBase(), "blueBlock.jpg");
    greenBlock = this.getImage (this.getDocumentBase(), "greenBlock.jpg");
    yellowBlock = this.getImage (this.getDocumentBase(), "yellowBlock.jpg");
    myfont = new Font("Arial",Font.BOLD,40); 
    myfont2 = new Font("Arial",Font.BOLD,30); 
    deadfont = new Font("Verdana",Font.BOLD, 60);
    
    appletHeight = 1024;
    appletWidth = 1280;
    offscreen = createImage(appletWidth, appletHeight); 
    bufferGraphics = offscreen.getGraphics(); 
    
  }
  
  // *****************************************************************
  
  public void start() 
  {
    // create a thread to do multi-tasking
    Thread myAnimation = new Thread (this);
    myAnimation.start();
  }
  
// *****************************************************************
  public void keyTyped(KeyEvent e){}
// *****************************************************************
  public void keyPressed(KeyEvent e){
    

    if (!gameStarted) {
      gameStarted = true;
      return;
    }
    
    int key = e.getKeyCode();
    
    if (key == 37){
      leftKey = true;
      
    }
    
    else if (key == 39){
      rightKey = true;
      
    }
    
    if (key == 32) {  // space bar
      
      spaceClicked = true;
    }
    
    if (lives == 0 && key == 27) { // ESC key
      
      init();
      System.out.println("reset the game");
      repaint();
      
    }
    
    
    
    repaint();
    e.consume();
    
  }
// *****************************************************************
  public void keyReleased(KeyEvent e) 
  {

    int key = e.getKeyCode();
    
    
    if (key == 37){
      leftKey = false;
      
    }
    
    else if (key == 39){
      rightKey = false;
      
    }
    
    
    
    
    
    
    // check for other arrow keys here
    repaint();
    e.consume();
    
  }
  // *****************************************************************
  
  public void paint (Graphics g)
  {
    
    bufferGraphics.drawImage(spaceBG,0,0,screenW, screenH, this); // this print the backround I am using the 0,0, because that is the starting  point of the image.
    
    
    if (!gameStarted) {
      bufferGraphics.setColor(Color.green);
      bufferGraphics.setFont(deadfont);
      bufferGraphics.drawString("BRICK BREAKER", 375, 200);
      bufferGraphics.drawString("PRESS ANY KEY TO START", 200, 800);
      bufferGraphics.setFont(myfont);
      bufferGraphics.setColor(Color.white);
      bufferGraphics.drawString("use the left & right arrow keys to move", 275, 850);
      bufferGraphics.setFont(myfont2);
      bufferGraphics.setColor(Color.white);
      bufferGraphics.drawString("A game by: Tashi Jampa", 460, 925);
    } 
    
    
    else {
      if (!spaceClicked && lives > 0){
        bufferGraphics.drawString("PRESS Space TO LAUNCH", 400, 500);
      }
      
      bufferGraphics.setColor(Color.white);
      bufferGraphics.setFont(myfont);
      bufferGraphics.drawString("Score: "+score,10,45);
      bufferGraphics.drawString("Level: "+lvl,10,900);
      bufferGraphics.drawImage(landingPad,landX, landY, landW, landH, this);
      bufferGraphics.drawImage(ball,ballX,ballY,ballW,ballH, this);
      
      //blocks *****************
      if(showRed1){
        bufferGraphics.drawImage(redBlock,redX,redY,redW,redH, this);
      }
      if (showRed2){
        bufferGraphics.drawImage(redBlock,redX2,redY2,redW2,redH2, this);
      }
      
      if (showRed3){
        bufferGraphics.drawImage(redBlock,redX3,redY3,redW3,redH3, this);
      }
      if (showRed4){
        bufferGraphics.drawImage(redBlock,redX4,redY4,redW4,redH4, this);
      }
      if (showRed5){
        bufferGraphics.drawImage(redBlock,redX5,redY5,redW5,redH5, this);
      }
      if (showBlue){
        bufferGraphics.drawImage(blueBlock,blueX,blueY,blueW,blueH, this);
      }
      if (showBlue2){
        bufferGraphics.drawImage(blueBlock,blueX2,blueY2,blueW2,blueH2, this);
      }
      if (showBlue3){
        bufferGraphics.drawImage(blueBlock,blueX3,blueY3,blueW3,blueH3, this);
      }
      if (showBlue4){
        bufferGraphics.drawImage(blueBlock,blueX4,blueY4,blueW4,blueH4, this);
      }
      if (showBlue5){
        bufferGraphics.drawImage(blueBlock,blueX5,blueY5,blueW5,blueH5, this);
      }
      if(showGreen){
        bufferGraphics.drawImage(greenBlock,greenX,greenY,greenW,greenH, this);
      }
      if(showGreen2){
        bufferGraphics.drawImage(greenBlock,greenX2,greenY2,greenW2,greenH2, this);
      }
      if(showGreen3){
        bufferGraphics.drawImage(greenBlock,greenX3,greenY3,greenW3,greenH3, this);
      }
      if(showGreen4){
        bufferGraphics.drawImage(greenBlock,greenX4,greenY4,greenW4,greenH4, this);
      }
      if(showGreen5){
        bufferGraphics.drawImage(greenBlock,greenX5,greenY5,greenW5,greenH5, this);
      }
      if(showYellow){
        bufferGraphics.drawImage(yellowBlock,yellowX,yellowY,yellowW,yellowH, this);
      }
      if(showYellow2){
        bufferGraphics.drawImage(yellowBlock,yellowX2,yellowY2,yellowW2,yellowH2, this);
      }
      if(showYellow3){
        bufferGraphics.drawImage(yellowBlock,yellowX3,yellowY3,yellowW3,yellowH3, this);
      }
      if(showYellow4){
        bufferGraphics.drawImage(yellowBlock,yellowX4,yellowY4,yellowW4,yellowH4, this);
      }
      if(showYellow5){
        bufferGraphics.drawImage(yellowBlock,yellowX5, yellowY5, yellowW5, yellowH5, this);
      }
      
      
      
      
      //*********************************
      
      if (lives == 0){
        
        bufferGraphics.setColor(Color.red);
        bufferGraphics.setFont(deadfont);
        bufferGraphics.drawString("GAME OVER", 435, 500);
        bufferGraphics.drawString("PRESS esc TO RESTART", 280, 700);
        bufferGraphics.setFont(myfont2);
        bufferGraphics.setColor(Color.white);
        bufferGraphics.drawString(" HIGH SCORE: "+score, 500,575);
        bufferGraphics.drawString(" BEST LEVEL: "+lvl, 500, 600);
      }
      if (lives >= 1){
        bufferGraphics.drawImage(heart, 1190, 10, this);
      }
      if (lives >= 2){
        bufferGraphics.drawImage(heart, 1120, 10, this);
      }
      if (lives == 3) {
        bufferGraphics.drawImage(heart, 1050, 10, this);
      } 
    }
    
    
    
    g.drawImage(offscreen,0,0, this);
  }
  // *****************************************************************
  
  public void update (Graphics g)
  {
    paint (g);
    
  }
  
  public void run() {
    while (true) {
      if (gameStarted == true){
        
        
        
        if (blockCounter == 0){
          spaceClicked = false;
          
          landX = 470;
          landY = 800;
          
          ballX = landX + landW / 2 - ballW / 2;
          ballY = landY - ballH;
          
          lvl ++;
          ballXS += 1;
          ballYS += 1;
          blockCounter = 20;
          
          showRed1 = true;
          showRed2 = true;
          showRed3 = true;
          showRed4 = true;
          showRed5 = true;
          showBlue = true;
          showBlue2 = true;
          showBlue3 = true;
          showBlue4 = true;
          showBlue5 = true;
          showGreen = true;
          showGreen2 = true;
          showGreen3 = true; 
          showGreen4 = true;
          showGreen5 = true;
          showYellow = true;
          showYellow2 = true;
          showYellow3 = true;
          showYellow4 = true;
          showYellow5 = true;
          
        }  
        
        
        
        
        //ball following before launch
        if (!spaceClicked){
          ballX = ballX = landX + landW / 2 - ballW / 2;
          ballY = landY - ballH;   
        }
        // *****************************************************************
        //landing pad movement
        
        if (leftKey && landX >= 0){
          landX -= 10; 
        }
        
        if (rightKey && landX <= screenW-landW){
          landX += 10; 
        }
        
        // *****************************************************************
        //ball and walls collisions
        // and when after the ball is launched
        
        
        if (spaceClicked){
          // Update ball position
          ballX += ballXS;
          ballY += ballYS;
          
          if (ballX <= 0 || ballX + ballSize >= screenW) {
            ballXS = -ballXS;  // reverse horizontal direction
            
          }
          
          if (ballY <= 0) {
            ballYS = -ballYS;  // reverse vertical direction
            
          }
          
          if (ballY + ballSize >= screenH){
            lives--;
            spaceClicked = false;
            
            landX = 470;
            landY = 800;
            
            ballX = landX + landW / 2 - ballW / 2;
            ballY = landY - ballH;
            
            
            
            
            try{Thread.sleep(300);}  
            catch (InterruptedException e) {}
          }
          
          
          // ***************************************************************** 
          // ball and block collisions 
          
          
          if  (lives > 0 && (collision(landX, landY, landW, landH, ballX, ballY, ballW,ballH))){
            // Always bounce upward
            ballYS = -Math.abs(ballYS);
            
            
            if (ballX + ballW / 2 > landX + landW / 2) {
              ballXS = 3;  // right side
              if (landW / 2 == ballX+ballW){
                ballYS = -ballYS;
              }
            } 
            
            
            
            
            else {
              ballXS = -3; // left side
              if (landW / 2 == ballX+ballW){
                ballYS = -ballYS;
              }
              
            }
            
            
          }
          
          
          
          if (showRed1 == true && collision(ballX, ballY, ballW, ballH, redX, redY, redW, redH)){
            ballYS = -ballYS; // reverse vertical direction
            showRed1 = false;
            score+=1; 
            blockCounter--;
            
          }
          
          if (showRed2 == true && collision(ballX, ballY, ballW, ballH, redX2, redY2, redW2, redH2)){
            ballYS = -ballYS; // reverse vertical direction
            showRed2 = false;
            score+=1;
            blockCounter--;
            
          }
          
          if (showRed3 == true && collision(ballX, ballY, ballW, ballH, redX3, redY3, redW3, redH3)){
            ballYS = -ballYS; // reverse vertical direction
            showRed3 = false;
            score+=1; 
            blockCounter--;
            
          }
          
          if (showRed4 == true && collision(ballX, ballY, ballW, ballH, redX4, redY4, redW4, redH4)){
            ballYS = -ballYS; // reverse vertical direction
            showRed4 = false;
            score+=1; 
            blockCounter--;
            
          }
          
          if (showRed5 == true && collision(ballX, ballY, ballW, ballH, redX5, redY5, redW5, redH5)){
            ballYS = -ballYS; // reverse vertical direction
            showRed5 = false;
            score+=1; 
            blockCounter--;
            
          }
          
          if (showBlue == true && collision(ballX, ballY, ballW, ballH, blueX, blueY, blueW, blueH)){
            ballYS = -ballYS; // reverse vertical direction
            showBlue = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showBlue2 == true && collision(ballX, ballY, ballW, ballH, blueX2, blueY2, blueW2, blueH2)){
            ballYS = -ballYS; // reverse vertical direction
            showBlue2 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showBlue3 == true && collision(ballX, ballY, ballW, ballH, blueX3, blueY3, blueW3, blueH3)){
            ballYS = -ballYS; // reverse vertical direction
            showBlue3 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showBlue4 == true && collision(ballX, ballY, ballW, ballH, blueX4, blueY4, blueW4, blueH4)){
            ballYS = -ballYS; // reverse vertical direction
            showBlue4 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showBlue5 == true && collision(ballX, ballY, ballW, ballH, blueX5, blueY5, blueW5, blueH5)){
            ballYS = -ballYS; // reverse vertical direction
            showBlue5 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showGreen == true && collision(ballX, ballY, ballW, ballH, greenX, greenY, greenW, greenH)){
            ballYS = -ballYS; // reverse vertical direction
            showGreen = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showGreen2 == true && collision(ballX, ballY, ballW, ballH, greenX2, greenY2, greenW2, greenH2)){
            ballYS = -ballYS; // reverse vertical direction
            showGreen2 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showGreen3 == true && collision(ballX, ballY, ballW, ballH, greenX3, greenY3, greenW3, greenH3)){
            ballYS = -ballYS; // reverse vertical direction
            showGreen3 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showGreen4 == true && collision(ballX, ballY, ballW, ballH, greenX4, greenY4, greenW4, greenH4)){
            ballYS = -ballYS; // reverse vertical direction
            showGreen4 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showGreen5 == true && collision(ballX, ballY, ballW, ballH, greenX5, greenY5, greenW5, greenH5)){
            ballYS = -ballYS; // reverse vertical direction
            showGreen5 = false;
            score+=1; 
            blockCounter--;
            
          }
          
          if (showYellow == true && collision(ballX, ballY, ballW, ballH, yellowX, yellowY, yellowW, yellowH)){
            ballYS = -ballYS; // reverse vertical direction
            showYellow = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showYellow2 == true && collision(ballX, ballY, ballW, ballH, yellowX2, yellowY2, yellowW2, yellowH2)){
            ballYS = -ballYS; // reverse vertical direction
            showYellow2 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showYellow3 == true && collision(ballX, ballY, ballW, ballH, yellowX3, yellowY3, yellowW3, yellowH3)){
            ballYS = -ballYS; // reverse vertical direction
            showYellow3 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showYellow4 == true && collision(ballX, ballY, ballW, ballH, yellowX4, yellowY4, yellowW4, yellowH4)){
            ballYS = -ballYS; // reverse vertical direction
            showYellow4 = false;
            score+=1; 
            blockCounter--;
            
          }
          if (showYellow5 == true && collision(ballX, ballY, ballW, ballH, yellowX5, yellowY5, yellowW5, yellowH5)){
            ballYS = -ballYS; // reverse vertical direction
            showYellow5 = false;
            score+=1; 
            blockCounter--;
            
          }
          
          
        }//space click boolean
      }//game started boolean
      
      repaint(); // calls the paint method to be run.
      try {Thread.sleep(15);}
      catch(InterruptedException e) {}
      
      
      
      
      
      
    } // while loop
  } // run method
  //*********************************************************
  
  private boolean collision (int x1, int y1, int width1, int height1, int x2, int y2, 
                             int width2, int height2) {
    
// method: collison
// this method will check if two objects have collided. If they have collided it 
// will return true else it will return false.
// input required: 
// provide the dimensions and co-ordinates of box 1: x1, y1, width1, height1
// provide the dimensions and co-ordinates of box 2: x2, y2, width2, height2  note: 
// set width2 and height2 to 1 if you are checking for mouse click inside a box.
    //
    //             (x2,y2). ------------------. (x2+width2, y2)
    //                    |                   |
    //                    |                   |
    //                    |                   |
    //     (x2,y2+height2).-------------------. (x2+width2, y2+height2)
    //
    //
    if (x1 + width1 <= x2 || x2 + width2 <= x1 || 
        y1 + height1<= y2 || y2 + height2 <= y1) 
      
      return false; // No collision
    else
      return true; // Collision detected
    
    
    
  }
  
  
  
}
