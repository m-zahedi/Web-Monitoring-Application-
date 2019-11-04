
#include <string.h>
#include <stdio.h>
#include <stdlib.h>
#include <winsock2.h>
#include <winsock.h>
#include <windows.h>
#include <time.h>
#include <winsock.h>

int up =0;
int  down=0;



char get_str(char * c) {
  int i = 0;
  for (i = 0; (*(c + i) = getchar()) != '\n'; i++);
  *(c + i) = '\0';
  return *c;
}

int get_int() {
  int i;
  int count = 10;
  char c = 1;
  int  res = 0;
  int temp = 10000;
  for (i = 0; ((c) = getchar()) != '\n'; i++) {
    res = res + ((c - '0')*temp / count);
    count *= 10;
  }
  res /= (temp / count) * 10;
  return res;
}

int main(){
	system("color 09");
    char name_addres_file[300];
    FILE *fptr;
    int url_number = 0, i = 0;
    fptr=fopen(name_addres_file,"a");
    printf("                        IN THE NAME OF GOD                   \n ");
    printf("\n              Welcome to the webSiteMonitoring App            \n");
    Sleep (4000);
    system("cls");
    system("color 09");
    puts("                         Please Enter A Text File To Save The Data : ");
    puts("\n                   for example : C:\\Users\\Desktop\\New Text Document.txt \n");
    get_str(name_addres_file);
    system("cls");
    system("color 09");
    puts("                              please enter email address                      ");
    char email_address[100];
    get_str(email_address);
    system("cls");
    system("color 09");
    puts(" \n\n\n                       How Many URLs Do You Want To Monitor?                ");
    url_number = get_int();
    system("cls");
    system("color 09");
    for (i = 0; i < url_number; i++) {
      char name_address[100];
      char time[10];
      int time_of_monitore;
      int clock;
      puts("\n\n\n\n                   Please Enter Name Address Or Addresses : ");
      get_str(name_address);
      system("cls");
      system("color 09");
      puts(" \n\n\n               How Many Times Do You Want To Monitor The Web Sites? :");
      time_of_monitore = get_int();
      system("cls");
      system("color 09");
      puts("\n\n\n\n            Please Enter Second (s) Or Minute (m) Forms To Be Searched : ");
      get_str(time);
      system("cls");
      system("color 09");
      puts("\n\n\n\n                How Many Seconds Or Minutes Do You Want To Monitor? :");
      clock = get_int();
      system("cls");
      system("color 09");

    if (time[0] == 's' || time[0] == 'S')
      clock *= 1000;
        else
    if (time[0] == 'm' || time[0] == 'M')
         clock *= 60 * 1000;

      while (time_of_monitore > 0) {
      fclose(fptr);
        connect_url(name_address,name_addres_file);
        Sleep(clock);
        time_of_monitore -= 1;
      }
      //_________________________________________________
      int k;
      send_email(email_address, name_addres_file);
      printf("\n\n\n\n");
      Sleep(5000);
      system("cls");
      system("color 09");
      printf("up    ");
      for (k=0;k<up;k++){
    	  printf("___");
      }
      puts("\n");
      printf("Down: ");
      for (k=0;k<down;k++){
    	  printf("___");
      }
      puts("\n");
      printf("All:  ");
      for (k=0;k<(up+down);k++){
    	  printf("___");
      }
      puts("\n\n     for exit click inter     ");
      getchar();
      down=0;
      up=0;
      //_____________________________________________________
      Sleep (5000);
      system("cls");
      system("color 09");
    }
    char check[5];
        puts("\n\n\n\n                   Do You Want To Exit The WebSite Monitoring App? ");
        get_str(check);
        if (check[0]=='N' || check[0]=='n')
    return main ();

        Sleep(1000);
        system("cls");
        puts ("\n\n\n\n                        Thanks For Your Selection :)                              ");
        Sleep(3000);
        return 0;
}

int  connect_url(char url[],char name_addres_file[]) {
  FILE *fptr;
  fptr = fopen(name_addres_file,"a");
    WSADATA wsa;
    SOCKET s;
    struct sockaddr_in server;
    time_t rawtime;
    struct tm * timeinfo;
    fprintf(fptr,"%s","\n initializing the WinSock ...");
    printf("\n initializing the WinSock ...");
    if (WSAStartup(MAKEWORD(2, 2), &wsa) != 0) {
    fprintf(fptr,"%s","failed.ERROR CODE :%d", WSAGetLastError());
      printf("failed.ERROR CODE :%d", WSAGetLastError());
      fclose(fptr);
      return 1;
    }
    printf("initialized.\n");
    fprintf(fptr,"%s","initialized.\n");
    if ((s = socket(AF_INET, SOCK_STREAM, 0)) == INVALID_SOCKET) {
    fprintf(fptr,"%s","could not create a socket:%d", WSAGetLastError());
      printf("could not create a socket:%d", WSAGetLastError());
    }
    struct hostent *lh;
    lh = gethostbyname(url);
    if (lh == NULL) {
      DWORD dwError;
      dwError = WSAGetLastError();
      if(dwError != 0) {
        if (dwError == WSAHOST_NOT_FOUND) {
          fprintf(fptr,"%s",url);
          fprintf(fptr,"%s","Host not found    or  system Not connected \n");
          fprintf(fptr,"__________________________________\n");
          printf("\a");
          printf("Host not found or system Not connected\n");
          fclose(fptr);
          return 1;
        }
        else
          if(dwError == WSANO_DATA) {
          fprintf(fptr,"%s","No data record found\n");
          printf("No data record found\n");
          fclose(fptr);
          return 1;
        }
        else {
          fprintf(fptr,"%s","Function failed with error: %d\n", dwError);
          printf("Function failed with error: %d\n", dwError);
          fclose(fptr);
          return 1;
        }
    }
}

      server.sin_addr.s_addr = inet_addr((inet_ntoa(*((struct in_addr *)lh->h_addr))));//IP
      server.sin_family = AF_INET;
      server.sin_port = htons(80);
      time (&rawtime);
      timeinfo = localtime (&rawtime);
      if (connect(s, (struct sockaddr *)&server, sizeof(server))<0) {
        fprintf(fptr,"%s","connect error\n");
        down+=1;
        puts("connect error");
    fclose(fptr);
        return 1;
      }
    fprintf(fptr,"%s",url);
    fprintf(fptr,"%s","\nconnected\n");
    puts("\nconnected");
    up+=1;
    fprintf(fptr,("%s", asctime (timeinfo)));
    fprintf(fptr,"__________________________________\n");
    printf ( "\ncurrent date and time of monitor : %s", asctime (timeinfo) );
    fclose(fptr);
    WSACleanup();
        return 0;
}

int send_email(char email_address[],char name_addres_file[]){
SOCKET conn;
FILE *fptr;
char text_for_send[1000];
fptr=fopen(name_addres_file,"r");
int i=0;
for(i=0;(fgetc(fptr))!=EOF;i++){
	text_for_send[i]=fgetc(fptr);
}
text_for_send[i]=0;
fscanf(fptr,"%s",text_for_send);
int lun,err = 0;
SOCKADDR_IN conn_addr;  //use
WSADATA data;
WORD ver;
LPHOSTENT host;  //use
  ver = MAKEWORD(2,0); //use
  WSAStartup(ver,&data);   //use
  conn = socket(PF_INET,SOCK_STREAM,0);   //use
  conn_addr.sin_family = AF_INET;   //use
  conn_addr.sin_port = htons(25);  //use
  host = gethostbyname(email_address);  //use
  if(host == NULL){
  err = WSAGetLastError();
  printf("Errore host\t%d",err);
  return 1;
  }
  conn_addr.sin_addr =*((LPIN_ADDR)*host-> h_addr_list);    //use
  connect(conn,(struct sockaddr*)&conn_addr,sizeof(struct sockaddr)); //use
  send(conn,text_for_send , strlen(text_for_send), 0);   //use
  closesocket(conn);
  WSACleanup();
  return 0;
  }
