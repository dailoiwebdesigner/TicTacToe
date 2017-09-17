/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package ttt;

import java.awt.Button;
import java.awt.GridLayout;
import java.awt.Point;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.List;
import javax.swing.JButton;
import javax.swing.JFrame;
import javax.swing.JOptionPane;


public class TicTacToe extends JFrame implements ActionListener{
    
    public String first_Click;
    public int dem = 0;
    public int kq = 1;
    public int trangthai = 0;
    public JButton btn = new JButton();
    AI ai = new AI();
    //JButton btn = new JButton();
    //JButton btn = new JButton();
    //Button pnlbtn = new Button();
    
//    for(int y = 1; y <= 9; y++){
//        buttons[y] = new JButton("");
//        pnlbtn.add(button[i]);
//    }
//    pnlbtn.setLayout(new GridLayout(3, 3));
//    for(int i=0;i<=8;i++){
//        buttons[i]=new JButton("");
//        pnlbtn.add(buttons[i]);
//        buttons[i].setBackground(SystemColor.menu);
//        buttons[i].addActionListener(this);
//    }
    


    

    private final JButton btn1 = new JButton();
    private final JButton btn2 = new JButton();
    private final JButton btn3 = new JButton();
    private final JButton btn4 = new JButton();
    private final JButton btn5 = new JButton();
    private final JButton btn6 = new JButton();
    private final JButton btn7 = new JButton();
    private final JButton btn8 = new JButton();
    private final JButton btn9 = new JButton();
    
    
    public TicTacToe(){
        
//        for(int i = 1; i <= 3; i++){
//        for(int j = 1; j <=3; j++){
//            btn[i][j] = new JButton();
//       }
//    }
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);  // cửa sổ bật tắt trên giao diện
        setSize(600, 600);                               
        setLayout(new GridLayout(3,3));                  
        setLocationRelativeTo(null);                     // khi build lên thì ngay vị trí giữa màn hình
        setVisible(true);                                // Đk để của sổ được hiện
        
        // đưa button ra màn hình
        add(btn1);
        add(btn2);
        add(btn3);
        add(btn4);
        add(btn5);
        add(btn6);
        add(btn7);
        add(btn8);
        add(btn9);
        
        
        
        //tạo sự kiện cho button
        btn1.addActionListener(this);
        btn2.addActionListener(this);
        btn3.addActionListener(this);
        btn4.addActionListener(this);
        btn5.addActionListener(this);
        btn6.addActionListener(this);
        btn7.addActionListener(this);
        btn8.addActionListener(this);
        btn9.addActionListener(this);
        
    }
//    public void luotDanh(String first_Click){
//        if(first_Click == "X"){
//            first_Click  = "O";
//        }
//        else first_Click = "X";
//    }
    
          
    @Override
    public void actionPerformed(ActionEvent e) {
        //throw new UnsupportedOperationException("Not supported yet."); //To change body of generated methods, choose Tools | Templates.
        
        /*
        Phần này để đếm xem: nếu số chẵn thì X đánh, nếu số lẻ thì O đánh 
        */
       if(trangthai == 0){
            if(e.getSource() == btn1){
            //System.out.println("x: "+btn1.getX()+"    y:"+ btn1.getY());
            btn1.setText("X");      // Xét quân cờ xem đánh X hay O
            ai.mang[0][0] = 1;
            btn1.setEnabled(false);         // Sau khi đánh thì xét cho button tắt để không thể nhấn lần 2
            winGame();                      // kiểm tra X hay O win hay hòa cờ 
            //inmang();
            
        }
        if(e.getSource() == btn2){
            //System.out.println("x: "+btn2.getX()+"    y:"+ btn2.getY());

            btn2.setText("X");
            ai.mang[0][1] = 1;
            btn2.setEnabled(false);
            winGame();

            //inmang();
        }
        if(e.getSource() == btn3){
            //System.out.println("x: "+btn3.getX()+"    y:"+ btn3.getY());

            btn3.setText("X");
            ai.mang[0][2] = 1;
            btn3.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn4){
            //System.out.println("x: "+btn4.getX()+"    y:"+ btn4.getY());

            btn4.setText("X");
            ai.mang[1][0] = 1;
            btn4.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn5){
            //System.out.println("x: "+btn5.getX()+"    y:"+ btn5.getY());

            btn5.setText("X");
            ai.mang[1][1] = 1;
            btn5.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn6){
        //System.out.println("x: "+btn6.getX()+"    y:"+ btn6.getY());

            btn6.setText("X");
            ai.mang[1][2] = 1;
            btn6.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn7){
            //System.out.println("x: "+btn7.getX()+"    y:"+ btn7.getY());
            btn7.setText("X");
            ai.mang[2][0] = 1;
            btn7.setEnabled(false);
            winGame();
            //inmang();
            //btn7.setEnabled(true);
        }
        if(e.getSource() == btn8){
            //System.out.println("x: "+btn8.getX()+"    y:"+ btn8.getY());
            btn8.setText("X");
            ai.mang[2][1] = 1;
            btn8.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn9){
            //System.out.println("x: "+btn9.getX()+"    y:"+ btn9.getY());
            btn9.setText("X");
            ai.mang[2][2] = 1;
            btn9.setEnabled(false);
            winGame();
            //inmang();

        }
        if( kq != 0){
            ai.giaTri_totNhat = 100;
            ai.Cat_tia(0, -10, ai.giaTri_O);
            if(ai.PointAI.x == 0 && ai.PointAI.y == 0){
                btn1.setText("O");
                btn1.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }

            if(ai.PointAI.x == 0 && ai.PointAI.y == 1){
                btn2.setText("O");
                btn2.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }
            if(ai.PointAI.x == 0 && ai.PointAI.y == 2){
                btn3.setText("O");
                btn3.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }
            if(ai.PointAI.x == 1 && ai.PointAI.y == 0){
                btn4.setText("O");
                btn4.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }
            if(ai.PointAI.x == 1 && ai.PointAI.y == 1){
                btn5.setText("O");
                btn5.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }
            if(ai.PointAI.x == 1 && ai.PointAI.y == 2){
                btn6.setText("O");
                btn6.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }
            if(ai.PointAI.x == 2 && ai.PointAI.y == 0){
                btn7.setText("O");
                btn7.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }if(ai.PointAI.x == 2 && ai.PointAI.y == 1){
                btn8.setText("O");
                btn8.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }
            if(ai.PointAI.x == 2 && ai.PointAI.y == 2){
                btn9.setText("O");
                btn9.setEnabled(false);
                ai.mang[ai.PointAI.x][ai.PointAI.y] = ai.giaTri_O;
                winGame();
            }
        }
        //winGame();
        //ai.khoiTao();
       }
       else{
        dem++;
        if(dem == 1 || dem == 3 || dem == 5 ||  dem == 7 || dem == 9){
            first_Click = "X";
        }
        else if(dem == 2 || dem == 4 || dem == 6 || dem == 8){
            first_Click = "O";
        }
        
        if(e.getSource() == btn1){
            //System.out.println("x: "+btn1.getX()+"    y:"+ btn1.getY());
            btn1.setText(first_Click);      // Xét quân cờ xem đánh X hay O
            btn1.setEnabled(false);         // Sau khi đánh thì xét cho button tắt để không thể nhấn lần 2
            winGame();                      // kiểm tra X hay O win hay hòa cờ 
            //inmang();
            
        }
        if(e.getSource() == btn2){
            //System.out.println("x: "+btn2.getX()+"    y:"+ btn2.getY());

            btn2.setText(first_Click);
            btn2.setEnabled(false);
            winGame();

            //inmang();
        }
        if(e.getSource() == btn3){
            //System.out.println("x: "+btn3.getX()+"    y:"+ btn3.getY());

            btn3.setText(first_Click);
            btn3.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn4){
            //System.out.println("x: "+btn4.getX()+"    y:"+ btn4.getY());

            btn4.setText(first_Click);
            btn4.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn5){
            //System.out.println("x: "+btn5.getX()+"    y:"+ btn5.getY());

            btn5.setText(first_Click);
            btn5.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn6){
            //System.out.println("x: "+btn6.getX()+"    y:"+ btn6.getY());

            btn6.setText(first_Click);
            btn6.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn7){
            //System.out.println("x: "+btn7.getX()+"    y:"+ btn7.getY());
            btn7.setText(first_Click);
            btn7.setEnabled(false);
            winGame();
            //inmang();
            //btn7.setEnabled(true);
        }
        if(e.getSource() == btn8){
            //System.out.println("x: "+btn8.getX()+"    y:"+ btn8.getY());
            btn8.setText(first_Click);
            btn8.setEnabled(false);
            winGame();
            //inmang();
        }
        if(e.getSource() == btn9){
            //System.out.println("x: "+btn9.getX()+"    y:"+ btn9.getY());
            btn9.setText(first_Click);
            btn9.setEnabled(false);
            winGame();
            //inmang();

        }
       }
    }
    
    public void winGame(){
        kq = 1;
        List<Point> ds = ai.danhsach();
        String b1 = btn1.getText();
        String b2 = btn2.getText();
        String b3 = btn3.getText();
        String b4 = btn4.getText();
        String b5 = btn5.getText();
        String b6 = btn6.getText();
        String b7 = btn7.getText();
        String b8 = btn8.getText();
        String b9 = btn9.getText();
        if(b1 == "X" && b2 == "X" && b3 == "X" || b4 == "X" && b5 == "X" && b6 == "X" || b7 == "X" && b8 == "X" && b9 == "X" || b1 == "X" && b5 == "X" && b9 == "X" || b7 == "X" && b5 == "X" && b3 == "X" || b1 == "X" && b4 == "X" && b7 == "X" || b2 == "X" && b5 == "X" && b8 == "X" || b3 == "X" && b6 == "X" && b9 == "X"){
            JOptionPane.showMessageDialog(rootPane, "Người chơi X win");
            kq = 0;
            int choiLai = JOptionPane.showConfirmDialog(rootPane, "Bạn có muốn chơi lại", "Chơi lại",  JOptionPane.YES_NO_OPTION);
            if(choiLai == JOptionPane.YES_OPTION){
                Reset();  
            }
        }
        else if(b1 == "O" && b2 == "O" && b3 == "O" || b4 == "O" && b5 == "O" && b6 == "O" || b7 == "O" && b8 == "O" && b9 == "O" || b1 == "O" && b5 == "O" && b9 == "O" || b7 == "O" && b5 == "O" && b3 == "O" || b1 == "O" && b4 == "O" && b7 == "O" || b2 == "O" && b5 == "O" && b8 == "O" || b3 == "O" && b6 == "O" && b9 == "O"){
            JOptionPane.showMessageDialog(rootPane, "Người chơi O win");
            kq = 0;
            int choiLai = JOptionPane.showConfirmDialog(rootPane, "Bạn có muốn chơi lại", "Chơi lại",  JOptionPane.YES_NO_OPTION);
            if(choiLai == JOptionPane.YES_OPTION){
                Reset();
            }
        }
        else if(ds.isEmpty()){
            JOptionPane.showMessageDialog(rootPane, "Hòa cờ");
            kq = 0;
            int choiLai = JOptionPane.showConfirmDialog(rootPane, "Bạn có muốn chơi lại", "Chơi Lại", JOptionPane.YES_NO_OPTION);
            if(choiLai == JOptionPane.YES_OPTION){
                Reset();
            }
        }
    }
    
//    public void inmang(){
//        for(int d=0; d<3; d++){
//            for(int l=0; l<3; l++)
//                System.out.printf("%d ",btn[d][l]);
//            System.out.println("");
//        }
//    }
    
//    public void setGiatri(int k, Boolean check_x){
//        if(check_x){
//            btn[k / 3][k %3 ] = 1;
//        }
//        else btn[k/3][k%3] = -1;
//        
//    }
    
    public void Reset(){
        new TicTacToe();
//        btn1.setText(null);
//        btn2.setText(null);
//        btn3.setText(null);
//        btn4.setText(null);
//        btn5.setText(null);
//        btn6.setText(null);
//        btn7.setText(null);
//        btn8.setText(null);
//        btn9.setText(null);
//        
//        btn1.setEnabled(true);
//        btn2.setEnabled(true);
//        btn3.setEnabled(true);
//        btn4.setEnabled(true);
//        btn5.setEnabled(true);
//        btn6.setEnabled(true);
//        btn7.setEnabled(true);
//        btn8.setEnabled(true);
//        btn9.setEnabled(true);
//        
//        dem = 0;
    }
//        for(int i = 1; i <= 9; i++){
//                String Tam;
//                Tam = btn[i].getText();}
//        else if(Tam != null){
//                
//            JOptionPane.showMessageDialog(rootPane, "Hòa cờ");
//            
//        }
    
//    public boolean wingame(){
//        if(winGame() == true){
//            
//        }
//    }
    
//    public boolean chuaDanh(){
//        for(int i = 1; i <= 9; i++){
//            boolean[] btn = null;
//            if(btn[i])
//        }
//        return true;
//    } 
//    public void hienBtn(){
//        for(int i = 1; i <= 9; i++){
//            btn[i].setEnabled(false);
//        }
//    }
    
    
    
    public static void main(String []agrs){
        new TicTacToe();
    }
}


