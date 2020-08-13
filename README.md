# samplecode
#include<stdio.h>
#include<stdlib.h>
void main()
{
       char user_name[20],password[20],confirm_password[20];
       int index , flag = 0, counter=1;
       FILE *fptr;
       printf("Remember->YOU HAVE ONLY TWO ATTEMPTS FOR TYPING THE CORRECT PASSWORD.\n");
       printf("Enter User Name:");
       gets(user_name);
       while(counter<=2)
       {
       		printf("attempt:%d\n",counter);
       		printf("Enter your password:");
       		gets(password);	
       		printf("Confirm password:");
       		gets(confirm_password);
		    for(index=0; password[index]!='\0'; index++){
              		if(password[index] != confirm_password[index]){
              		   flag = 1;
	                   break; 
              		}
       		}
       		flag = flag==0 && confirm_password[index] == '\0' ? 0 : 1;
		    if(flag == 0){
		       printf("Both passwords are same.\n");
		       fptr=fopen("user.dat","w");
		       for(index = 0; user_name[index] != '\0'; index++){
	       			fputc(user_name[index],fptr);
      		        }
		       for(index = 0; password[index]!='\0';index++){
			       fputc(password[index],fptr);
		       }
		       fclose(fptr);
	           break;
	       }
	       else{
		       printf("Both passwords are not same.\n");
	       }
		  counter++;
       }

}
