# Linux Account Add Makefile
#
# Make sure your mysql library is either called 'libmysqlclient' or you have
# a link named such pointing to the proper client library,
# like libmysqlclient.so -> libmysqlclient.so.18

ifeq ($(OS),Windows_NT) 
    MYSQL = -L../mysql/lib -llibmysql
else
    MYSQL = -lmysqlclient
endif

CFLAGS = 
CC = gcc

account-add: account_add.o md5.o
	$(CC) $(CFLAGS) -o $@ $< -L/usr/lib/x86_64-linux-gnu $(MYSQL) md5.o

account_add.o: account_add.c
	$(CC) $(CFLAGS) -I../mysql/include -I../md5/include -c account_add.c

md5.o: ../md5/md5.c
	$(CC) $(CFLAGS) -c $<

clean:
	rm *.o
