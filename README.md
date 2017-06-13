# Find-Root-for-third-degree-polynomials-
Find Roots for third degree polynomials in Pascal (except imaginary roots)
program PROJETONUMERICO;
 USES CRT;

   VAR
	    INTER: ARRAY[1..3] OF INTEGER;
	    AUX: ARRAY[1..6] OF INTEGER;
       K2, AU,AU2,OP,OP2, PA,Q,V,H,J,I,E, K:INTEGER;
      WRES2, WRES, RES, M2,N2,L2,M,N,L,A,B,FS,VI,VAI,FNI,IMM,FN,IM1,X0,IM,W1,C,W,X,X1,X3,F,G,D:REAL;
          
          FUNCTION RAIZ (R:INTEGER;A,B,M,N:REAL; VAR KI:REAL):REAL;
            
		BEGIN
          CASE R OF
            1: BEGIN   
		   F:=M*SIN(A); 
		   G:=M*SIN(B);		   	   
		   END;
            2: BEGIN
		   F:=M*COS(A);
		   G:=M*COS(B);
		   END;
		  3: BEGIN
		   F:=M*LN(A);
		   G:=M*LN(B);
		   END;
		  4: BEGIN
		   F:=M*EXP(A);
		   G:=M*EXP(B);
		   END;
		  5:BEGIN
		   F:=M*SQR(A);
		   G:=M*SQR(B);
		   END;
		  6:BEGIN
		   F:=M*A;
		   G:=M*B;
		   END;
		  7:BEGIN
		   F:=M*SIN(A)+N*COS(A);
		   G:=M*SIN(B)+N*COS(B);
		   END;
		  8:BEGIN
		   F:=M*SIN(A)+N*LN(A);
		   G:=M*SIN(B)+N*LN(B);
		   END;
		  9:BEGIN
		   F:=M*SIN(A)+N*EXP(A);
		   G:=M*SIN(B)+N*EXP(B);
		   END;
		  10:BEGIN
		   F:=M*SIN(A)+N*SQR(A);
		   G:=M*SIN(B)+N*SQR(B);
		   END;
		  11:BEGIN
		   F:=M*SIN(A)+N*A;
		   G:=M*SIN(B)+N*B;
		   END;
		  12:BEGIN
		   F:=M*SIN(A)+N;
		   G:=M*SIN(B)+N;
		   END;
		  13:BEGIN
		   F:=M*COS(A)+N*LN(A);
		   G:=M*COS(B)+N*LN(B);
		   END;
		  14:BEGIN
		   F:=M*COS(A)+N*EXP(A);
		   G:=M*COS(B)+N*EXP(B);
		   END;
		  15:BEGIN
		   F:=M*COS(A)+N*SQR(A);
		   G:=M*COS(B)+N*SQR(B);
		   END;
		  16:BEGIN
		   F:=M*COS(A)+N*A;
		   G:=M*COS(B)+N*B;
		   END;
		  17:BEGIN
		   F:=M*COS(A)+N;
		   G:=M*COS(B)+N;
		   END;
		  18:BEGIN
		   F:=M*LN(A)+N*EXP(A);
		   G:=M*LN(B)+N*EXP(B);
		   END;
		  19:BEGIN
		   F:=M*LN(A)+N*SQR(A);
		   G:=M*LN(B)+N*SQR(B);
		   END;
		  20:BEGIN
		   F:=M*LN(A)+N*A;
		   G:=M*LN(B)+N*B;
		   END;
		  21:BEGIN
		   F:=M*LN(A)+N;
		   G:=M*LN(B)+N;
		   END;
		  22:BEGIN
		   F:=M*EXP(A)+N*SQR(A);
		   G:=M*EXP(B)+N*SQR(B);
		   END;
		  23:BEGIN
		   F:=M*EXP(A)+N*A;
		   G:=M*EXP(B)+N*B;
		   END;
		  24:BEGIN
		   F:=M*EXP(A)+N;
		   G:=M*EXP(B)+N;
		   END;
		  25:BEGIN
		   F:=M*SQR(A)+N*A;
		   G:=M*SQR(B)+N*B;
		   END;
		  26:BEGIN
		   F:=M*SQR(A)+N;
		   G:=M*SQR(B)+N;
		   END;
		  27:BEGIN
		   F:=M*A+N;
		   G:=M*B+N;
		   END;  		                      
            END;
           
             RAIZ:=F*G;
             KI:=G;             
          END;
          
          FUNCTION NEWTON (R:INTEGER; A,M,N:REAL; VAR KI:REAL):REAL;
		
		BEGIN
          CASE R OF
            1: BEGIN   
		   F:=M*SIN(A); 
		   D:=M*COS(A);
		   END;
            2: BEGIN
		   F:=M*COS(A);
		   D:=-M*SIN(A);
		   END;
		  3: BEGIN
		   F:=M*LN(A);
		   D:=M*(1/A);
		   END;
		  4: BEGIN
		   F:=M*EXP(A);
		   D:=M*EXP(A);
		   END;
		  5:BEGIN
		   F:=M*SQR(A);
		   D:=2*M*A;
		   END;
		  6:BEGIN
		   F:=M*A;
		   D:=M;
		   END;
		  7:BEGIN
		   F:=M*SIN(A)+N*COS(A);
		   D:=M*COS(A)-N*SIN(A);
		   END;
		  8:BEGIN
		   F:=M*SIN(A)+N*LN(A);
		   D:=M*COS(A)+N*(1/A);
		   END;
		  9:BEGIN
		   F:=M*SIN(A)+N*EXP(A);
		   D:=M*COS(A)+N*EXP(A);
		   END;
		  10:BEGIN
		   F:=M*SIN(A)+N*SQR(A);
		   D:=M*COS(A)+N*2*A;
		   END;
		  11:BEGIN
		   F:=M*SIN(A)+N*A;
		   D:=M*COS(A)+N;
		   END;
		  12:BEGIN
		   F:=M*SIN(A)+N;
		   D:=M*COS(A);
		   END;
		  13:BEGIN
		   F:=M*COS(A)+N*LN(A);
		   D:=-M*SIN(A)+N*(1/A);
		   END;
		  14:BEGIN
		   F:=M*COS(A)+N*EXP(A);
		   D:=-M*SIN(A)+N*EXP(A);
		   END;
		  15:BEGIN
		   F:=M*COS(A)+N*SQR(A);
		   D:=-M*SIN(A)+N*2*A;
		   END;
		  16:BEGIN
		   F:=M*COS(A)+N*A;
		   D:=-M*SIN(A)+N;
		   END;
		  17:BEGIN
		   F:=M*COS(A)+N;
		   D:=-M*SIN(A);
		   END;
		  18:BEGIN
		   F:=M*LN(A)+N*EXP(A);
		   D:=M*(1/A)+N*EXP(A);
		   END;
		  19:BEGIN
		   F:=M*LN(A)+N*SQR(A);
		   D:=M*(1/A)+N*2*A;
		   END;
		  20:BEGIN
		   F:=M*LN(A)+N*A;
		   D:=M*(1/A)+N;
		   END;
		  21:BEGIN
		   F:=M*LN(A)+N;
		   D:=M*(1/A);
		   END;
		  22:BEGIN
		   F:=M*EXP(A)+N*SQR(A);
		   D:=M*EXP(A)+N*2*A;
		   END;
		  23:BEGIN
		   F:=M*EXP(A)+N*A;
		   D:=M*EXP(A)+N;
		   END;
		  24:BEGIN
		   F:=M*EXP(A)+N;
		   D:=M*EXP(A);
		   END;
		  25:BEGIN
		   F:=M*SQR(A)+N*A;
		   D:=M*2*A+N;
		   END;
		  26:BEGIN
		   F:=M*SQR(A)+N;
		   D:=M*2*A;
		   END;
		  27:BEGIN
		   F:=M*A+N;
		   D:=M;
		   END;  		                      
            END;           
          
		   NEWTON:=A-F/D;
		   KI:=F;


	   END;
             
	    FUNCTION SECANTE (R,PA:INTEGER; A,B,M,N:REAL; VAR KI:REAL):REAL;
	    
	    
	       BEGIN
          CASE R OF
            1: BEGIN   
		   F:=M*SIN(A); 
		   G:=M*SIN(B);		   	   
		   END;
            2: BEGIN
		   F:=M*COS(A);
		   G:=M*COS(B);
		   END;
		  3: BEGIN
		   F:=M*LN(A);
		   G:=M*LN(B);
		   END;
		  4: BEGIN
		   F:=M*EXP(A);
		   G:=M*EXP(B);
		   END;
		  5:BEGIN
		   F:=M*SQR(A);
		   G:=M*SQR(B);
		   END;
		  6:BEGIN
		   F:=M*A;
		   G:=M*B;
		   END;
		  7:BEGIN
		   F:=M*SIN(A)+N*COS(A);
		   G:=M*SIN(B)+N*COS(B);
		   END;
		  8:BEGIN
		   F:=M*SIN(A)+N*LN(A);
		   G:=M*SIN(B)+N*LN(B);
		   END;
		  9:BEGIN
		   F:=M*SIN(A)+N*EXP(A);
		   G:=M*SIN(B)+N*EXP(B);
		   END;
		  10:BEGIN
		   F:=M*SIN(A)+N*SQR(A);
		   G:=M*SIN(B)+N*SQR(B);
		   END;
		  11:BEGIN
		   F:=M*SIN(A)+N*A;
		   G:=M*SIN(B)+N*B;
		   END;
		  12:BEGIN
		   F:=M*SIN(A)+N;
		   G:=M*SIN(B)+N;
		   END;
		  13:BEGIN
		   F:=M*COS(A)+N*LN(A);
		   G:=M*COS(B)+N*LN(B);
		   END;
		  14:BEGIN
		   F:=M*COS(A)+N*EXP(A);
		   G:=M*COS(B)+N*EXP(B);
		   END;
		  15:BEGIN
		   F:=M*COS(A)+N*SQR(A);
		   G:=M*COS(B)+N*SQR(B);
		   END;
		  16:BEGIN
		   F:=M*COS(A)+N*A;
		   G:=M*COS(B)+N*B;
		   END;
		  17:BEGIN
		   F:=M*COS(A)+N;
		   G:=M*COS(B)+N;
		   END;
		  18:BEGIN
		   F:=M*LN(A)+N*EXP(A);
		   G:=M*LN(B)+N*EXP(B);
		   END;
		  19:BEGIN
		   F:=M*LN(A)+N*SQR(A);
		   G:=M*LN(B)+N*SQR(B);
		   END;
		  20:BEGIN
		   F:=M*LN(A)+N*A;
		   G:=M*LN(B)+N*B;
		   END;
		  21:BEGIN
		   F:=M*LN(A)+N;
		   G:=M*LN(B)+N;
		   END;
		  22:BEGIN
		   F:=M*EXP(A)+N*SQR(A);
		   G:=M*EXP(B)+N*SQR(B);
		   END;
		  23:BEGIN
		   F:=M*EXP(A)+N*A;
		   G:=M*EXP(B)+N*B;
		   END;
		  24:BEGIN
		   F:=M*EXP(A)+N;
		   G:=M*EXP(B)+N;
		   END;
		  25:BEGIN
		   F:=M*SQR(A)+N*A;
		   G:=M*SQR(B)+N*B;
		   END;
		  26:BEGIN
		   F:=M*SQR(A)+N;
		   G:=M*SQR(B)+N;
		   END;
		  27:BEGIN
		   F:=M*A+N;
		   G:=M*B+N;
		   END;  		                      
            END;          
            IF ((F-G)=0) THEN 
		  BEGIN
		  PA:=1;
            END;
            IF ((F-G)<>0) THEN
            BEGIN
	       SECANTE:=(B*F-A*G)/(F-G);
		   KI:=F;
		  END;
		     
		 END;   	
         
 Begin
	   Q:=0;
	   OP:=0;
	   OP2:=1;
	   
	   REPEAT
        WRITELN('                       OPCOES DE FUNCOES :');
        WRITELN(' ');
        WRITELN(' 1 :M*SENX;         2 :M*COSX;           3 :M*LNX;            4 :M*eX;');
        WRITELN(' 5 :M*X2;           6 :M*X;              7 :M*SENX+N*COSX;    8 :M*SENX+N*LNX;');
        WRITELN(' 9 :M*SENX+N*eX;    10 :M*SENX+N*X2;     11 :M*SENX+M*X;      12 :M*SENX+N;');
        WRITELN(' 13 :M*COSX+N*LNX;  14 :M*COSX+N*eX;     15 :M*COSX+N*X2;     16 :M*COSX+N*X;');
        WRITELN(' 17 :M*COSX+N;      18 :M*LNX+N*eX;      19 :M*LNX+N*X2;      20 :M*LNX+N*X;');
        WRITELN(' 21 :M*LNX+N;       22 :M*eX+N*X2;       23 :M*eX+N*X;        24 :M*eX+N;');
        WRITELN(' 25 :M*X2+N*X;      26 :M*X2+N;          27 :M*X+N');
        WRITELN(' ');


		
		
		 REPEAT
		  IF (OP2=1) THEN
		  BEGIN
		 WRITELN('DIGITE A OPCAO DE FUNCAO , VER TABELA ACIMA E DIGITE O NUMERO DA FUNCAO DESEJADA:');
		 READLN(K);
		 WRITELN('DIGITE AS CONSTANTES M E N RESPECTIVAMENTE DESEJADAS NA FUNCAO, CASO N NAO EXISTA DIGITE QUALQUER VALOR PARA ELA:');
		 READLN(M,N);
           WRITELN('DIGITE O INTERVALO DESEJADO NA FUNCAO TAL QUE O MODULO DO INTERVALO SEJA IGUAL A 1, DIGITANDO O MAIOR NUMERO PRIMEIRO :');
           READLN(X,X1);
		  IF (X>X1) THEN
		   BEGIN
		   L:=X-X1;
		   END;
		  IF (X1>X) THEN
		   BEGIN
		   WRITELN('DIGITE O MAIOR NUMERO PRIMEIRO');
		   WRITELN(' ');
		   L:=10;
		   END;
		   K2:=K;
             L2:=L;
             M2:=M;
             N2:=N;
            END;
            IF (OP2=0) THEN
             BEGIN
             K:=K2;
             L:=L2;
             M:=M2;
             N:=N2;
             END;
     IF ((K=3) AND ((X+X1)=0)) OR ((K=3) AND (X<0) AND (X1<0)) OR ((K=8) AND ((X+X1)=0)) OR ((K=8) AND (X<0) AND (X1<0)) OR
     ((K=13) AND ((X+X1)=0)) OR ((K=13) AND (X<0) AND (X1<0)) OR ((K=18) AND ((X+X1)=0)) OR ((K=18) AND (X<0) AND (X1<0)) OR
     ((K=19) AND ((X+X1)=0)) OR ((K=19) AND (X<0) AND (X1<0)) OR ((K=20) AND ((X+X1)=0)) OR ((K=20) AND (X<0) AND (X1<0)) OR
     ((K=21) AND ((X+X1)=0)) OR ((K=21) AND (X<0) AND (X1<0))  THEN
       BEGIN
       L:=10;
       WRITELN(' O INTERVALO ESCOLHIDO POSSUI LOGARITIMO DE NUMERO NEGATIVO OU IGUAL A ZERO, POR FAVOR REPITA AS ESCOLHAS');
       END;
       IF ((K=5) OR ((K=10) AND (M=0)) OR ((K=15) AND (M=0)) OR ((K=19) AND (M=0)) OR ((K=22) AND (M=0)) OR ((K=25) AND (N=0)) OR
	  ((K=26) AND (N=0)))  THEN
       BEGIN
       WRITELN(' A FUNCAO X AO QUADRADO SO TEM COMO RAIZ O ZERO, REPITA AS ESCOLHAS ');
       L:=10;
       END;
       IF ((K=4) OR ((K=14) AND (M=0)) OR ((K=9) AND (M=0)) OR ((K=18) AND (M=0)) OR ((K=22) AND (N=0)) OR ((K=23) AND (N=0)) OR
	  ((K=24) AND (N=0)))  THEN
       BEGIN
       WRITELN(' A FUNCAO EXPONENCIAL SO TEM COMO RAIZ O MENOS INFINITO, INCALCULAVEL , REPITA AS ESCOLHAS ');
       L:=10;
       END;
          IF ((L=1) AND (OP2=0)) OR ((L=1) AND (OP2=1)) THEN 
          BEGIN
           WRITELN('DIGITE 1, 2 ,3 OU 4 PARA OPCAO DE METODO PARA ACHAR A RAIZ DA FUNCAO:');
           WRITELN(' 1 : METODO DA BISSECAO ');
           WRITELN(' 2 : METODO DE NEWTON ');
           WRITELN(' 3 : METODO DAS SECANTES ');  
           WRITELN(' 4 : TODOS OS METODOS ');
           READLN(V);
		   W:=RAIZ(K,X,X1,M,N,IM);
		   IF (W>0) THEN 
		   BEGIN
		   WRITELN('NAO EXISTE RAIZ NO INTERVALO');
		   END;
		  END;
		  RES:=((X+X1)/2); 
		  WRES:=RAIZ(K,X,RES,M,N,IM);
		  WRES2:=RAIZ(K,RES,X1,M,N,IM);
		  IF (WRES=0) OR (WRES2=0) THEN
		  BEGIN
		  IF ((WRES=0) AND (WRES2=0)) THEN
		  BEGIN
		  WRITELN(' A RAIZ ESTA ESTA EXATAMENTE NO MEIO DO INTERVALO, IGUAL A , ',RES:1:20,' ');
		  WRITELN(' ');
		  END;
		  IF ((WRES=0) AND (WRES2<>0)) THEN
		  BEGIN
		  WRITELN(' A RAIZ ESTA NO INTERVALO ESCOLHIDO E E IGUAL A , ', X:1:20,' ');
		  WRITELN(' ');
		  END;
		  IF ((WRES<>0) AND (WRES2=0)) THEN
		  BEGIN
		  WRITELN(' A RAIZ ESTA NO INTERVALO ESCOLHIDO E E IGUAL A , ', X1:1:20,' ');
		  WRITELN(' ');
		  END;
		  L:=10;
		  END; 
		 UNTIL (W<0)AND(L=1);  
		 
		  REPEAT          
             X3:=(X+X1)/2;                    
          W:=RAIZ(K,X,X3,M,N,IM);
            IF W<0 THEN
            BEGIN
              X1:=X3;
            END;
            IF (W>0) THEN
            BEGIN
             X:=X3;
            END;
              L:=X1-X;
            UNTIL (W<0)AND (L<=0.1);         
             A:=X; B:=X1;      
               IF (V=1) OR (V=4) THEN BEGIN
		   REPEAT
               I:=I+1;
                J:=0;    
               C:=(X+X1)/2;
               W1:=RAIZ(K,X,C,M,N,IM);
               IF W1<0 THEN
                BEGIN
                  X1:=C;
                  END;
                 IMM:=ABS(IM);
			IF W1>0 THEN
			BEGIN
			    X:=C;
			  END; 
			IF IMM<=1/1000000 THEN
			BEGIN
			  J:=1;
			END;                
                    
             UNTIL  (I=100) OR (J=1) ;
                  IF I=100 THEN
                  BEGIN
			    W1:=RAIZ (K,X,C,M,N,IM);
			    END;  
               
             WRITELN('METODO DA BISSECAO RAIZ: ',C:1:20);
             WRITELN('METODO DA BISSECAO IMAGEM: ', IM:1:20);
             WRITELN('METODO DA BISSECAO N DE ITERACOES: ',I);
             WRITELN(' ');
             INTER[1]:=I;
             END;
              IF (V=2) OR (V=4) THEN BEGIN
             I:=0;
             X0:=(A+B)/2;
              REPEAT
               I:=I+1;
               J:=0;
               FN:=NEWTON (K,X0,M,N,IM1);
               X0:=FN;
               VAI:=ABS(IM1);
               IF VAI<=1/1000000 THEN
               BEGIN
               J:=1;
               VAI:=IM1;
               END;
               
             UNTIL (I=100)OR (J=1);
              IF I=100 THEN 
              FNI:=NEWTON (K,X0,M,N,VAI);
             WRITELN('METODO DE NEWTON RAIZ: ',X0:1:20);
             WRITELN('METODO DE NEWTON IMAGEM: ',VAI:1:20);
             WRITELN('METODO DE NEWTON N DE ITERACOES: ',I);
		   WRITELN(' '); 
		   INTER[2]:=I;  
                  END;
               IF (V=3) OR (V=4) THEN BEGIN
		    I:=0;E:=1; 
           REPEAT
              J:=0;
              I:=I+1;
              FS:=SECANTE (K,Q,A,B,M,N,VI);
              B:=A;
              A:=FS;
              VAI:=ABS(VI);
              IF VAI<=1/1000000 THEN
               BEGIN
                 J:=1;
               END;
             UNTIL (I=100)OR (J=1) OR (Q=1);
              IF I=100 THEN
              BEGIN
              FS:=SECANTE (K,Q,A,E,M,N,VI);
              END;
              IF (Q=1) THEN BEGIN
              WRITELN('O METODO DAS SECANTES NAO FUNCIONOU POIS HOUVE UMA DIVISAO POR ZERO NAS ITERACOES NO INTERVALO ESCOLHIDO');
              WRITELN(' ');
              END;
             IF (Q=0) THEN BEGIN 
		   WRITELN('METODO DA SECANTE RAIZ:',A:1:20);
		   WRITELN('METODO DA SECANTE IMAGEM: ',VI:1:20);
		   WRITELN('METODO DA SECANTE N DE ITERACOES: ',I);
		   WRITELN(' ');
		   INTER[3]:=I;
		   END;
             END;
              IF V=4 THEN
              BEGIN
              IF Q=0 THEN
              BEGIN
		    AUX[1]:=0; AUX[2]:=101;
		    AUX[3]:=101; 
               FOR AU:=1 to 3 DO
                BEGIN
                 IF (INTER[AU]>=AUX[1]) THEN
                  BEGIN
                  AUX[1]:=INTER[AU];
                  AUX[4]:=AU;
                  END;
                 IF (INTER[AU]<=AUX[3]) THEN
                  BEGIN
                  AUX[3]:=INTER[AU];
                  AUX[6]:=AU;
                  END;
                END;
               AUX[5]:=1;
               FOR AU:=1 TO 2 DO
                BEGIN
                 IF (AUX[5]=AUX[4]) OR (AUX[5]=AUX[6]) THEN
                  BEGIN
                  AUX[5]:=AUX[5]+1;
                  END;
                END;
               AUX[2]:=INTER[AUX[5]];
               WRITELN(' ');
			WRITELN('OS METODOS EM ORDEM CRESCENTE DE MAIS EFICIENTE SEGUEM ABAIXO: ');
			WRITELN('METODO ',AUX[6],' COM ',AUX[3],' ITERACOES '); 
			WRITELN('METODO ',AUX[5],' COM ',AUX[2],' ITERACOES '); 
			WRITELN('METODO ',AUX[4],' COM ',AUX[1],' ITERACOES '); 
			WRITELN(' ');
              END;
              END;
              IF Q=1 THEN
              BEGIN
              IF INTER[1]>INTER[2] THEN
               BEGIN
               WRITELN('OS METODOS EM ORDEM CRESCENTE DE MAIS EFICIENTE SEGUEM ABAIXO: ');
               WRITELN('METODO ',2,' COM ',INTER[2],' ITERACOES ');
               WRITELN('METODO ',1,' COM ',INTER[1],' ITERACOES ');
               WRITELN(' ');
               WRITELN('O METODO DAS SECANTES NAO HOUVE ITERACOES ');
               WRITELN(' ');
               END;
              IF INTER[2]>=INTER[1] THEN
               BEGIN
               WRITELN('OS METODOS EM ORDEM CRESCENTE DE MAIS EFICIENTE SEGUEM ABAIXO: ');
               WRITELN('METODO ',1,' COM ',INTER[1],' ITERACOES ');
               WRITELN('METODO ',2,' COM ',INTER[2],' ITERACOES ');
               WRITELN(' ');
               WRITELN('O METODO DAS SECANTES NAO HOUVE ITERACOES ');
               WRITELN(' ');
               END;
              END;
             WRITELN(' ');
             WRITELN('DESEJA REUTILIZAR O PROGRAMA ? SE SIM DIGITE 0 SENAO DIGITE 1');
             READLN(OP);
              IF ((OP=0) AND (V<>4)) THEN
              BEGIN
              WRITELN('DESEJA REUTILIZAR OS DADOS E SOMENTE UTILIZAR OUTRO METODO ? SE SIM DIGITE 0 SENAO DIGITE 1');
              READLN(OP2);
              END;
             
           UNTIL (OP<>0) ;
END.
 
 
