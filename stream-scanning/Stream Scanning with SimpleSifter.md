# NOT READY FOR PRODUCTION, WORK IN PROGRESS

# stream Scanning with SimpleSifter

SimpleSifter is the next step up from phone or webcam scanning, and is the most reliable way to scan directly into SortSwift from any Fujitsu or Ricoh compatible scanner.  While we recommend the Ricoh fi-8170 Scanner to take full advantage of Sortswift [(you can read more about our hardware recommendations here)](https://sortswift.com/features/hardware), many small-to-medium sized sellers can find value in SimpleSifter with smaller starting investments. 

SimpleSifter offers two ways to scan your cards into SortSwift:

1. **Stream scanning** - Enables scanning cards directly into the SwiftSort application

2. **Batch scanning** - Enables creation of "batches" of cards to import into SortSwift at a later time

This documentation will focus on stream scanning. [For more info on batch scanning, see the batch scanning documentation]()

*NOTE: To follow this documentation you will need to have SimpleSifter already started and running, which requires a fujitsu-compatible scanner and a Raspberry Pi.  [You can find our detailed setup documentation here.](https://scribehow.com/viewer/How_to_Install_and_use_the_Simple_Sifter__Ih_iNfYkTySnw453BZ4mdQ)*

## Step 1 - Prepare to Scan

As a best-practice tip to help you make the most of SimpleSifter without sorting hardware, pre-sorted your cards by game, set, and finish.

Set and finish are not required...in fact SortSwift's AI does a pretty fantastic job of matching cards to specific sets and even detecting card finishes.  

However, if manually sorted before scanning, you can configure these constraints on your scanner settings in the SimpleSifter UI to (foil, etched foil, etc) to reduce or eliminate most of the manual intervention that might be required in cases where AI confidence might be low due to multiple finishes, printings, or other variations for a particular card

![An image of the scanner configuration in SimpleSifter, highlighting the options to lock the printing/finish of a card as well as the set](image-1.png)

Once you have your constraints configured, click "Start" to begin feeding cards into the scanner.  

*NOTE: You can set the "Count" value in the UI to "0" to have the scanner scan continually until there are no physical cards remaining, or you can set a different value to scan a specific number of cards at a time.*

![alt text](image.png)

## Step 2 - Choose to Stream Scan or Batch Scan

Once you have your constraints configured, click "Start" to begin feeding cards into the scanner.  

*NOTE: You can set the "Count" value in the UI to "0" to have the scanner scan continually until there are no physical cards remaining, or you can set a different value to scan a specific number of cards at a time.*

![alt text](image.png)

If configured for "0" count, the scanner will continue to accept new cards without needing intervention in the UI.  If the scanner runs out of cards, the process will simply pause and resume immediately as soon as new cards are detected in the scanner.

#### Checking the Scan Progress

As cards are being scanned, you can track the progress 

