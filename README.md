# WiFly
Resource at www.barryvandam.com/getting-started-with-wifly-i
Used mBed with 'pass through' serial program:
#include "mbed.h"
 
Serial pc(USBTX, USBRX);
Serial uart(p9, p10);
 
DigitalOut pc_activity(LED1);
DigitalOut uart_activity(LED2);
 
int main() {
    while(1) {
        if(pc.readable()) {
            uart.putc(pc.getc());
            pc_activity = !pc_activity;
        }
        if(uart.readable()) {
            pc.putc(uart.getc());
            uart_activity = !uart_activity;
        }
    }
}

WiFlyt connbections
mBed     WiFly
gnd------pin p18 & p19
Vout-----pin 20 & pin 21
p9--------
p10-------

Commands
$$$  put in command mode
get wlan
set wlan ssid virginmedia5958900
set wlan phrase wdbdnnml
set wlan join 1  - auto join mode
set wlan channel 0  - all channels
set ip dhcp 0  - off, manual ip
set ip address 192.168.0.250  - ensure out of dhcp range
save
join
reboot

try ping 192.168.0.250 to see if connected
