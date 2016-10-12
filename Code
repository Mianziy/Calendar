//this program is aimed to make a Calendar
#define _CRT_SECURE_NO_WARNINGS
#include<stdio.h>
#include<stdlib.h>

int getmonthdays(year, month)
{
	if (month == 1 || month == 3 || month == 5 ||
		month == 7 || month == 8 || month == 10 || \
		month == 12)
	{
		return 31;
	}
	else if (month == 2)
	{
		if (isleapyear(year))
		{
			return 29;
		}
		else
		{
			return 28;
		}
	}
	else
	{
		return 30;
	}
}

int dateinput() // return the value xxxxxxxx for xxxx/xx/xx (yr/mon/day)
{
	int year, month, day;
	printf("please input date (use RETURN or two SPACE to devide)\n");
	scanf("%d%d%d", &year, &month, &day);
	if ((year > 9999 || year < 1900) || (month > 12 || month < 0) ||\
		(day > getmonthdays(year, month) || day < 0))
	{
		printf("WARNING:WRONG DATE \n");
		return 0;
	}
	printf("your input date: %d/%d/%d\n", year, month, day);
	return 10000 * year + 100 * month + day;
}

int isleapyear(year)  // 0 for not leap year, 1 for leap year
{
	if (year % 400 == 0)
	{
		return 1;
	}
	else if (year % 100 != 0 && year % 4 == 0)
	{
		return 1;
	}
	else
	{
		return 0;
	}
}

int dayscount(year, month, day)
{
	int sum = 0;
	for (int i = 1900; i < year; i++)
	{
		if (isleapyear(i))
		{
			sum = sum + 366;
		}
		else
		{
			sum = sum + 365;
		}
	}
	for (int j = 1; j < month; j++)
	{
		if (isleapyear(year))
		{
			if (j == 1 || j == 3 || j == 5 || \
				j == 7 || j == 8 || j == 10 || \
				j == 12)
			{
				sum = sum + 31;
				continue;
			}
			else if (j == 2)
			{
				sum = sum + 29;
				continue;
			}
			else
			{
				sum = sum + 30;
				continue;
			}
		}
		else if (!isleapyear(year))
		{
			if (j == 1 || j == 3 || j == 5 || \
				j == 7 || j == 8 || j == 10 || \
				j == 12)
			{
				sum = sum + 31;
				continue;
			}
			else if (j == 2)
			{
				sum = sum + 28;
				continue;
			}
			else
			{
				sum = sum + 30;
				continue;
			}
		}
	}
	sum = sum + day - 1;
	printf("form 1900/01/01, %d days passed\n", sum);

	return sum;
}

void titleprint()
{
	printf("the calender of this month as following\n"
		"\n"
		"*********************************\n"
		"MON  TUE  WEN  THU  FRI  STA  SUN\n");
}

void monthprint(int firstdayvalue, int monthdays)
{
	int i = firstdayvalue + 1;
	int space = 5 * (i - 1);
	for (int spc = 1; spc <= space; spc++)
	{
		printf(" ");
	}
	for (int j = 1; j <= monthdays; j++)
	{
		if (i>7)
		{
			printf("\n");
			i = 1;
		}
		printf("%d", j);
		if (j < 10 && i < 7)
		{
			printf("    ");
		}
		else if (j >= 10 && i < 7)
		{
			printf("   ");
		}
		i++;
	}
}

void main()
{
	int date, isleap, year, month, day, weekvalue, firstdayvalue, monthdays;
	int sum = 0;
	char *str[7] = { "MON", "TUE", "WEN", "THU", "FRI", "STA" };
	date = dateinput();
	if (date == 0)
	{
		printf("\n***********\n   ERROR\n***********\n");
	}
	else
	{
		year = date / 10000;
		month = (date % 10000) / 100;
		day = date % 100;
		isleap = isleapyear(year);
		sum = dayscount(year, month, day);
		weekvalue = sum % 7;
		printf("the date is %s\n", str[weekvalue]);
		sum = sum - day + 1;
		firstdayvalue = sum % 7;
		printf("the first day of this month is %s\n", str[firstdayvalue]);
		monthdays = getmonthdays(year, month);
		printf("this month has %d days\n", monthdays);
		titleprint(date);
		monthprint(firstdayvalue, monthdays);
		printf("\n*********************************\n");
	}
	system("pause");
}
