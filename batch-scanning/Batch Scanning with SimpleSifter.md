# Batch Scanning with SimpleSifter

SimpleSifter is the next step up from phone or webcam scanning, and is the most reliable way to scan directly into SortSwift from any Fujitsu or Ricoh compatible scanner.  While we recommend the Ricoh fi-8170 Scanner to take full advantage of Sortswift [(you can read more about our hardware recommendations here)](https://sortswift.com/features/hardware), many small-to-medium sized sellers can find value in SimpleSifter with smaller starting investments. 

SimpleSifter offers two ways to scan your cards into SortSwift:

1. **Stream scanning** - Enables scanning cards directly into the SwiftSort application

2. **Batch scanning** - Enables creation of "batches" of cards to import into SortSwift at a later time

This documentation will focus on batch scanning. [For more info on stream scanning, see the stream scanning documentation]()

*NOTE: To follow this documentation you will need to have SimpleSifter already started and running, which requires a fujitsu-compatible scanner and a Raspberry Pi.  [You can find our detailed setup documentation here.](https://scribehow.com/viewer/How_to_Install_and_use_the_Simple_Sifter__Ih_iNfYkTySnw453BZ4mdQ)*

## Step 1 - Prepare to Scan

### Manual Preparation

As a best-practice tip to help you make the most of SimpleSifter without sorting hardware, pre-sorted your cards by game, set, and finish.

Set and finish are not required...in fact SortSwift's AI does a pretty fantastic job of matching cards to specific sets and even detecting card finishes.  

However, if manually sorted before scanning, you can configure these constraints on your scanner settings in the SimpleSifter UI to (foil, etched foil, etc) to reduce or eliminate most of the manual intervention that might be required in cases where AI confidence might be low due to multiple finishes, printings, or other variations for a particular card

![An image of the scanner configuration in SimpleSifter, highlighting the options to lock the printing/finish of a card as well as the set](image-1.png)

### Scanner Configuration

#### Mode
There are two scanning modes available:

1. **Scan Count** - Scans a specified number of cards before stopping 

***NOTE:** You can set the "Count" value in the UI to "0" to have the scanner scan continually until there are no physical cards remaining, or you can set a different value to scan a specific number of cards at a time.*

![alt text](image.png)

2. **Scan til Stop** - Scans cards one at a time, pausing between each card and checking for highly customizable "stop conditions" (Like card names, values, sets, etc) before continuing.  If a configured stop condition is triggered, the scanning will not resume without manual intervention.

![alt text](image-2.png)

***NOTE:** "Scan til Stop" pauses after every card scan before continuing while the AI checks for any configured stop conditions.  This makes this mode significantly slower than the "Scan Count" mode.*


In this documentation, we will scan normal-finish only cards from *Magic: The Gathering* set "AFR" in "Scan Count" mode with count "0" (continuous scan until user-initiated stop)

![alt text](image-3.png)

## Step 2 - Scanning Cards

#### Start Scanning
Click "Start" to begin scanning cards.  The scanner will consume the cards one at a time until:

1. The user manually stops/pauses scanning
2. The scanner cannot find a new card to scan (either a jam or out of cards)
3. The scan count, if set, is reached
4. A stop condition, if configured, is triggered

#### Checking the Scan Progress

As cards are being scanned, you can track the progress of the scanned cards by clicking on the most recent card image on the scanner settings.  This will open the scan history for the scanner, where you can see the AI detection progress of your scanned cards as well as information such as name, set, market prices, and more:

![alt text](image-4.png)

## Step 3 - Using the Batch Manager

Open the Batch Manager with the "Batch" button in the top right of the SimpleSifter UI.

![alt text](image-6.png)

***NOTE:** Batches are saved to the SimpleSifter (your Raspberry Pi) and NOT to SortSwift. We will cover moving these to SortSwift or exporting via CSV or XML in the next step*

SimpleSifter allows for an in-progress queue to be either cleared (you will not be able to recover scans which are cleared from the queue) saved as a new batch, or "swapped" for a previously saved batch using the previous batch's "Resume" feature.

![alt text](image-5.png)

Previously saved batches can be:

1. **Resumed** with the "Play" button - This replaces your active queue with the saved batch, marking the previously active queue as "Unsaved Batch" 

2. **Deleted** with the "Trash" button - Gone forever, be careful! You will not get these scans back in SortSwift

3. **Renamed** with the "Pencil" button

4. **Merged** into another batch with the "Link" button - Choosing option will open a new UI where you will select from your other batches to merge into the selected batch.

Once a batch is saved to your SimpleSifter, it can be imported into SortSwift for editing, adding to your SortSwift inventory, or exporting to another platform via CSV or XML.

## Step 4 - Importing a Batch into SortSwift

When you're ready to import a batch into SortSwift to make changes, import into your SortSwift inventory, or export via CSV or XML, ensure you are on the same network as your SimpleSifter, log into the SortSwift application and navigate to "Scanning -> Simple Sifter -> Simple Sifter"

![alt text](image-7.png)

#### Connecting the SimpleSifter

Toggle the SimpleSifter connection to "On" *(If asked, make sure to accept the certificate)*

![alt text](image-8.png)

Once you see "Status: Connected" you are ready to import a batch from SimpleSifter

#### Choosing a Batch

Use the "Load Batch" button to see pending batches on the connected SimpleSifter

![alt text](image-9.png)

Click any pending batch to load it's data into SortSwift.

***NOTE:** This does not remove the batch from SimpleSifter...the data persists there until manually deleted in the SimpleSifter UI.*

#### Working with an Imported Batch

![alt text](image-10.png)

Once the batch is imported, you'll see the list of the scanned cards and can sort by price, rarity, card name, AI confidence score, and more.

To edit an entry, click on it in the list and close the drawer by clicking to the right side of the screen.

![alt text](image-11.png)

To make changes to a card in the list, you can edit and of the associated fields with this list entry.  In our example, the AI flagged that it may have mislabeled the set.  To correct this, we can choose the correct set on the left side of the screen, then click "Approve" to push the change back to our list.

![alt text](image-12.png)

***NOTE:** Any changes will NOT update the batch in SimpleSifter, only the current list we're editing inside of SortSwift.*

## Step 5 - Importing into SortSwift Inventory, or Exporting to Another Location

When you're ready to export your active list to