
## Solution c++    
```c++
i char check() /* check who is winner */
 {
     int x=0,o=0,counter=0;
      for(int row=0;row<3;row++)
        {
          for(int colum=0;colum<3;colum++)
            {
                /*check in rows*/
                if  (Games[row][colum]='x')
                {
                    x++;
                }
                else if (Games[row][colum]='o')
                {
                    o++;
                }
                if(x==3)
                {
                    return 'x';//bt3ml function 3shan t7dd winner
                }
                  if(x==3)
                {
                    return 'o' ;
                }
            }
         x=0,o=0;
        }
        //-----------------------------------------------------------------------------------------------------------------------------
       for(int colum=0;colum<3;colum++)
        {
          for(int row=0;row<3;row++)
            {
                /*check in colums*/
                if  (Games[row][colum]='x')
                {
                    x++;
                }
                else if (Games[row][colum]='o')
                {
                    o++;
                }
                if(x==3)
                {
                    return 'x';
                }
                  if(x==3)
                {
                    return 'o' ;
                }
            }
         x=0,o=0;
        }
        //   check the main Diagonal
        if(Games[0][0]=='x' && Games[1][1]=='x' && Games[2][2]=='x')
        {
            return 'x';
        }
        if(Games[0][0]=='o' && Games[1][1]=='o' && Games[2][2]=='o')
        {
            return 'o';
        }
        //check the another Diagonal

        if(Games[0][2]=='x' && Games[1][1]=='x' && Games[2][0]=='x')
        {
            return 'x';
        }
                if(Games[0][2]=='o' && Games[1][1]=='o' && Games[2][0]=='o')
        {
            return 'o';
        }
        /*----------------------------------------------------------------------*/
      /* no winer*/

         for(int row=0;row<3;row++)
        {
          for(int colum=0;colum<3;colum++)
            {
                //mafysh amakn mta7h to play
                if(Games[row][colum]!='x' && Games[row][colum]!='o' ) 
                {
                   counter++;
                }
            }
        }
        if(counter==0) 
        {
            return'=';
        }
      return'*';// to enter in while
}


```

