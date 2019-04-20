##### ai-car-microbit controler-
let recv = ""
serial.onDataReceived(serial.delimiters(Delimiters.NewLine), function () {
    recv = serial.readUntil(serial.delimiters(Delimiters.NewLine))
    radio.sendString(recv)
    basic.showString(recv)
})
radio.onReceivedString(function (receivedString) {
    serial.writeLine(receivedString)
})
radio.setGroup(123)
serial.redirect(
    SerialPin.USB_TX,
    SerialPin.USB_RX,
    BaudRate.BaudRate115200
)
basic.showIcon(IconNames.Happy)
