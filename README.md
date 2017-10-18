# morse_code
/* Program to translate morse code to english and vice vesa*/
#include<stdio.h>
#include<string.h>
#include<ctype.h>
int main()
{
	char s[40]; //to store all the alphabets and digits
	int i;
	char ch='A',y='0';
	for(i=0;i<26;i++)
	{
		s[i]=ch;
		ch++;
	}
	for(y='1';y<='9';y++)
	{
		s[i]=y;
		i++;
	}
	s[i]='0';
	i++;
	s[i]='.';
	i++;
	s[i]='\0';
  
	char morse[40][7]; //to store the morse code for all alphabets and digits
	strcpy(morse[0],".-");
	strcpy(morse[1],"-...");
	strcpy(morse[2],"-.-.");
	strcpy(morse[3],"-..");
	strcpy(morse[4],".");
	strcpy(morse[5],"..-.");
	strcpy(morse[6],"--.");
	strcpy(morse[7],"....");
	strcpy(morse[8],"..");
	strcpy(morse[9],".---");
	strcpy(morse[10],"-.-");
	strcpy(morse[11],".-..");
	strcpy(morse[12],"--");
	strcpy(morse[13],"-.");
	strcpy(morse[14],"---");
	strcpy(morse[15],".--.");
	strcpy(morse[16],"--.-");
	strcpy(morse[17],".-.");
	strcpy(morse[18],"...");
	strcpy(morse[19],"-");
	strcpy(morse[20],"..-");
	strcpy(morse[21],"...-");
	strcpy(morse[22],".--");
	strcpy(morse[23],"-..-");
	strcpy(morse[24],"-.--");
	strcpy(morse[25],"--..");
	strcpy(morse[26],".----");
	strcpy(morse[27],"..---");
	strcpy(morse[28],"...--");
	strcpy(morse[29],"....-");
	strcpy(morse[30],".....");
	strcpy(morse[31],"-....");
	strcpy(morse[32],"--...");
	strcpy(morse[33],"---..");
	strcpy(morse[34],"----.");
	strcpy(morse[35],"-----");
	strcpy(morse[36],".-.-.-"); 
  
	char s2[80]; //to accept the string
	int c=0;  
	printf("Enter a string\n");
	scanf("%[^\n]s",s2);
  
	for(i=0;s2[i]!='\0';i++) //to check if the string accepted is in english language or morse code
		if(isalnum(s2[i]))
		{
			c++;
			break;
		}
    
	if(c!=0) //if string is in english
	{
		for(i=0;s2[i]!='\0';i++)
		{
			if((s2[i]==s[i])||(s2[i]==s[i]+32))
				printf("%s ",morse[i]);
			else if(s2[i]==' ')
				printf("/ ");
			else
				printf("# ");
		}
	}
	else //if string is in morse code
	{
		char temp[8]; //for extracting characters of the morse code until we get a space
		int j=0,k;
		for(i=0;s2[i]!='\0';i++)
		{
			if(s2[i]!=' ')
			{
				temp[j]=s2[i];
				j++;
			}
			if(s2[i]==' '||s2[i]=='\0')
			{
				temp[j]='\0';
				for(k=0;k<40;k++)
					if(strcmp(temp,morse[k])==0)
						printf("%c",s[k]);
				j=0;
			}
			if(strcmp(temp,"/")==0)
				printf(" ");
		}
	} 
	return 0;
}
