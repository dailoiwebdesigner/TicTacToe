# TicTacToe
/*
 * To change this license header, choose License Headers in Project Properties.
 * To change this template file, choose Tools | Templates
 * and open the template in the editor.
 */
package ttt;

import java.util.List;
import java.awt.Point;
import java.util.ArrayList;
import static java.util.Collections.list;

/**
 *
 * @author dailo
 */
public class AI {
    public int giaTri_X = 1;
    public int giaTri_O = -1;
    public int[][] mang = new int[3][3];
    public int giaTri_totNhat = 100;
    
    
    
    public void khoiTao_mangBandau(){
        for(int i = 0; i < 3; i++){
            for(int j = 0; j < 3; j++){
                mang[i][j] = 0;
                //System.out.println(mang[i][j]+"    ");
            }
        }
    }
    
    public int check_nutLa(){
        List<Point> ds = danhsach();
        for(int i = 0; i < 3; i++){
            if(mang[i][0] == mang[i][1] && mang[i][0] == mang[i][2] && mang[i][0] == giaTri_X){
                return 1;
            }
            if(mang[i][0] == mang[i][1] && mang[i][0] == mang[i][2] && mang[i][0] == giaTri_O){
                return -1;
            }
            
            if(mang[0][i] == mang[1][i] && mang[0][i] == mang[2][i] && mang[0][i] == giaTri_X){
                return 1;
            }
            if(mang[0][i] == mang[1][i] && mang[0][i] == mang[2][i] && mang[0][i] == giaTri_O){
                return -1;
            }
        }
        if(mang[0][0] == mang[1][1] && mang[0][0] == mang[2][2] && mang[0][0] == giaTri_X){
            return 1;
        }
        if(mang[0][0] == mang[1][1] && mang[0][0] == mang[2][2] && mang[0][0] == giaTri_O){
            return -1;
        }
        if(mang[0][2] == mang[1][1] && mang[0][2] == mang[2][0] && mang[0][2] == giaTri_X){
            return 1;
        }
        if(mang[0][2] == mang[1][1] && mang[0][2] == mang[2][0] && mang[0][2] == giaTri_O){
            return -1;
        }
        if(ds.isEmpty()){
            return 0;
        }
        return 10;
    }
    
    public List<Point> danhsach(){
        List<Point> ds = new ArrayList<Point>();
        for(int i = 0; i < 3; i++){
            for(int j = 0; j < 3; j++){
                if(mang[i][j] == 0){
                    ds.add(new Point(i, j));
                }
            }
        }
        return ds;
    }
    Point PointAI = null;
    
    public int Cat_tia(int Do_sau, int Vp, int thuocTinh){
        
//        for(int i = 0; i < 3; i++){
//            for(int j = 0; j < 3; j++){
//                
//                System.out.print(mang[i][j]  +"  ");
//                
//            }
//            System.out.println("");
//        }
        int Vq;
        int n = check_nutLa();
        
        if(n != 10){
//            for(int i = 0; i < 3; i++){
//                for(int j = 0; j < 3; j++){
//                    System.out.print(mang[i][j]+"     ");
//                    
//                }
//                System.out.println("   ");
//                    
//            }
//            System.out.println(n);
            return Vq = n; 
                
        }
        if(thuocTinh == 1){
            Vq = -10;
        }
        else Vq = 10;
        List<Point> ds = danhsach();
        for(int i = 0; i < danhsach().size(); i++){
            
            
            Point p = ds.get(i);
            mang[p.x][p.y] = thuocTinh;
            if(thuocTinh == giaTri_X){

                Vq = Math.max(Vq, Cat_tia(Do_sau+1, Vq, giaTri_O));
                
                mang[p.x][p.y] = 0;
                
                if(Vp <= Vq) return Vq;
            }
            else {    

                Vq = Math.min(Vq, Cat_tia(Do_sau+1, Vq, giaTri_X));
                mang[p.x][p.y] = 0;
                if(Do_sau == 0){
                    //moi System.out.println("do sau = 0      "+Vq);
                }
                if(Do_sau == 0 && Vq < giaTri_totNhat){
                    giaTri_totNhat = Vq;
                    //moi System.out.println("gtri tot nhat: "+giaTri_totNhat);
                    PointAI = p;
                //    System.out.println(Vq);
                }
                if(Vp >= Vq) return Vq;
            }
            
        }
        return Vq;
    }
    
    
}

