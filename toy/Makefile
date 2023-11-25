TARGET = toy_system

SYSTEM = ./system
UI = ./ui
WEB_SERVER = ./web_server

# 표준 디렉토리가 아닌 위치에 있는 헤더 파일의 디렉토리 지정
INCLUDES = -I$(SYSTEM) -I$(UI) -I$(WEB_SERVER)

CC = gcc
CFLAGS = -g -Wall

objects = main.o system_server.o web_server.o input.o gui.o

.PHONY: clean

$(TARGET): $(objects)
  # make ./bin/
  # IF bin already exists, continue building process
	@ mkdir ./bin 2> /dev/null || true
	$(CC) $(CFLAGS) -o $(TARGET) $(objects)
	@ mv $(TARGET) bin/

# gcc -c option
# separate compile시 많이 이용되는 option으로 
# 전처리, 컴파일, 어셈블까지 실행하여 object파일 만들기 
# linking은 않하고, object파일 까지 만들기 

main.o: main.c
	$(CC) -g $(INCLUDES) -c main.c

system_server.o: $(SYSTEM)/system_server.h  $(SYSTEM)/system_server.c
	$(CC) $(CFLAGS) -c $(INCLUDES) $(SYSTEM)/system_server.c

gui.o: $(UI)/gui.h $(UI)/gui.c
	$(CC) $(CFLAGS) -c $(INCLUDES) $(UI)/gui.c

web_server.o: $(WEB_SERVER)/web_server.h $(WEB_SERVER)/web_server.c
	$(CC) $(CFLAGS) -c $(INCLUDES) $(WEB_SERVER)/web_server.c

input.o: $(UI)/input.h $(UI)/input.c
	$(CC) $(CFLAGS) -c $(INCLUDES) $(UI)/input.c

clean:
	rm -fr *.o
	rm -fr bin/$(TARGET)
