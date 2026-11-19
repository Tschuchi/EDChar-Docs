# Players

## Your characters

In player mode the sidebar shows **Character Generator Earthdawn 1st Edition** and the **List of your Characters:**. Click a character to open it. While a character is open, the other characters are greyed out. To close the character, click the **X** at the top left of the main area.

Below the list are these buttons:

| Button | What it does | Available |
|---|---|---|
| **Create** | Creates a new character, see below | when no character is open |
| **Delete** | Opens **Delete a Character**. Choose the character and confirm *There is no going back! Delete '…'?* | when no character is open |
| **Export** | Downloads the open character as a `.edchar` file | when a character is open |
| **Import** | Loads a character from a `.edchar` file. If a character with the same name exists, a copy is created after you confirm. | always |
| **PDF Export** | Downloads the open character as a PDF character sheet | when a character is open |

!!! example "Screenshot: `player-character-list.png`"
    Sidebar with **List of your Characters:** and the buttons **Create**, **Delete**, **Export**, **Import**, **PDF Export**.

## Creating a character

Creating a character takes three steps.

**Step 1: Name, discipline and race**

1. Click **Create**. The dialog **Create a new Character** opens.
2. Enter a **Name** (at least 3 characters). The button **Next** appears in the name field. Click it.
3. Choose your discipline under **Select Discipline**. A description of the discipline appears below.
4. Choose your race under **Select Race**. A description of the race appears below.
5. Click **Next Step**.

!!! example "Screenshot: `player-create-step1.png`"
    Dialog **Create a new Character** with name, discipline and race selected.

**Step 2: Attributes**

The dialog **Character Attribute Values Distribution** shows the six attributes with **Base**, **Cost**, **Racial**, **Value** and **Step**. Raise and lower the base values. The total cost is shown as *… of max 72*. **Next Step** becomes available once all points are distributed.

!!! example "Screenshot: `player-create-step2.png`"
    Dialog **Character Attribute Values Distribution** with all points distributed.

**Step 3: Talents, spells and skills**

The dialog *Now increase the rank of your talents, learn spells and choose your Skills* explains what to do next. Click **Finish**. You then set talent ranks, spells and skills on the character sheet in the tab **Talents / Spells / Skills**.

If you click **Cancel** in step 2 or 3, the character created in step 1 is deleted again.

## The character sheet

When a character is open, the main area shows **Character Views** and a row of tabs. On narrow screens, scroll the row sideways.

| Tab | Content |
|---|---|
| **Base Values** | Discipline, race and circle, attributes, defenses, ratings, karma, description |
| **Talents / Spells / Skills** | Talents per circle, knacks, spells and matrices, skills, versatility |
| **Combat** | Macros, initiative and karma, attacks, spellcasting, damage |
| **Equipment** | Weapons, armor, loot and all other items, character picture |
| **Legend** | Legend points earned and spent |
| **Notes** | Your own documents for this character |
| **Campaign** | Only shown when the character belongs to a campaign |

!!! example "Screenshot: `player-sheet-tabs.png`"
    Character sheet with **Character Views** and the row of tabs.

### Base Values

The tab shows these boxes:

- **1st Discipline & Circle:** name, **Discipline:**, **Race:** and **Circle:**. Use **+** and **−** next to the circle to change it. When a new circle grants an attribute point, the dialog **Distribute 1 Attribute Point** opens. The pencil (tooltip **Edit Character Name**) changes the name.
- **Attributes:** the six attributes with racial modifier and step. The pencil (tooltip **Edit Attributes**) opens the attribute values.
- **Character Description:** sex, height, age, hair, eyes, appearance. Edit with the pencil (tooltip **Edit Character Description**).
- **2nd Discipline and Circle:** start a second discipline with **Start 2nd Discipline?**.
- **Base Defense Values & Armor**, **Death & Unconscious Rating**, **Wound Threshold & Recovery**, **Initiative**, **Movement & Carry/Lift Capacity**.
- **Permanent Wounds & Strain:** edit with the pencil (tooltip **Edit permanent Wounds and Strain**).
- **Karma Points:** current and maximum karma, **Karma Ritual**.
- **Special Abilities:** **Racial Abilities:** and **Discipline Abilities:**.
- **Description, personal quotes or anything noteworthy:** free text.

Under **Any other influences or improvements on your Base Values?** you enter bonuses from spells, items or other sources, for example a death rating bonus from Wood Skin. **Add Animal Companion?** and **Show Animal Companions** manage animal companions.

In **Wound Threshold & Recovery** you use recovery tests with **Use Rec. Test: Step … 🎲 …** and restore them with **8h Sleep**.

!!! example "Screenshot: `player-base-values.png`"
    Tab **Base Values** with the boxes **1st Discipline & Circle** and **Attributes**.

### Talents / Spells / Skills

- **Talents:** the talents of your discipline, grouped by circle. Raise or lower a rank with the arrow buttons (tooltips **Increase rank** and **Decrease rank**). The tooltip shows the legend point cost, for example *Increase cost … LP*. On touch devices, press and hold the button to see the cost. **Show only available Circles** and **Show all Circles** switch the view.
- **Talent Knacks:** add knacks with **Add Knacks**. There are **Standard Knacks** and **Custom Knacks**.
- **Spells:** add spells with **Add Spells**, create your own with **Create Custom Spell**. Sort with **Sort A-Z** or **Sort Circle**.
- **Matrices:** put spells into your spell matrices with **Edit Matrix**.
- **Skills:** add skills with **Add Skills**. There are **Standard Skills** and **Custom Skills**. Sort with **Sort A..Z** or **Sort Category**.
- **Versatility:** only for humans. Raise the rank of Versatility to add talents from other disciplines with **Add Versatility Talents**.

!!! example "Screenshot: `player-talents.png`"
    Tab **Talents / Spells / Skills** with talents of one circle and the cost tooltip.

### Dice and info search

The tabs **Base Values**, **Talents / Spells / Skills** and **Combat** contain two tools:

- **Throw Dice:** choose a step under *Select the step you need to throw dice for:*. The app shows the matching dice, for example *Step 8 = 🎲: …*. Click the dice button to roll; the result appears in a window.
- **Search for Infos of Disciplines, Passions, Talents or Spells:** under *What are you looking for?* choose **Discipline**, **Talent**, **Passion**, **Tal. Desc.**, **Spell** or **Spell Desc.** and enter a name or search term.

For rolls where karma can be used, the app asks *Do you want to use Karma for this roll?*. With two disciplines it also asks *Karma from which discipline?*.

!!! example "Screenshot: `player-dice.png`"
    Box **Throw Dice** and a dice result.

### Combat

- **Macros for Step Dice:** save frequent rolls as macros with **Add a Macro** (name, step, use karma, additional info). Switch between alphabetical and manual order, and move macros with **Move earlier** and **Move later**.
- **Ini & Karma Usage:** **Roll Ini** rolls the initiative, **Set Ini** sets it manually. Spend karma with **use Karma …**.
- **Choose your Attack and Cause some Damage!:** choose an attack talent with **Choose your Attack Talent!** or attack with **Just Dex!**. Enter a situational **Bonus/Malus**, roll the **Attack Roll**, mark **Hit** or **Miss**, then roll the **Damage Roll** with your weapon.
- **Casting a Spell:** choose a spell from your matrices or from **Spell Storage**, weave the threads (*How many threads to weave at once?*) and roll the spellcasting test.
- **Suffer Damage, Wounds & Healing:** enter **Damage taken**, choose the protection (**Phys. Armor** or **Myst. Armor**) and click **Apply Damage**. **Apply Healing**, **Rec. Test** and **Heal Wounds** reduce damage and wounds.
- **Combat Defense Values, Armor & Wound Threshold** and **Death / Uncon. Rating & Damage** show the current values.
- **Equipment that is used:** choose the weapon (**Select your weapon:**) and armor (**Select your armor:**) you use in combat.

!!! example "Screenshot: `player-combat.png`"
    Tab **Combat** with an attack roll.

### Equipment

The tab has one box per category: **Your Weapons**, **Your Armor**, **Your Loot**, **Your Bloodcharms**, **Your Magical Items**, **Your Thread Objects**, **Your other Items**, **Your Healing Aids**, **Your Provisions**, **Your Adventuring Items**, **Your Clothes**, **Your miscellaneous Items** and **Your picture**.

- Add items with the plus button of the box, for example **Add Weapons**, and choose from the list. *Can't find the item you're looking for? Add any item from the list and edit it afterwards to match what you need.*
- Click an item to see and edit its details. Delete it with the trash icon.
- **Your Loot:** add and spend money with **+ Loot** and **- Loot**.
- **Your picture:** upload a character picture. It also appears on the PDF character sheet.

!!! example "Screenshot: `player-equipment.png`"
    Tab **Equipment** with weapons and armor.

### Legend

The tab **Your Legend** lists your legend points.

- **Add Legend** opens **Add Legend Entry**: choose a date with **Select Date**, enter the **Points** and what they were for, choose **Earned Points** or **Spent Points** and click **Save Entry**.
- The top shows **Earned Legendpoints** and **Spent Legendpoints** and *You have … LP to spend.*
- **Calulate Spent LP** calculates the legend points spent on attribute increases, talent ranks, skill ranks and starting a second discipline. Legend points spent on karma or threads are not included.
- Click an entry to see or edit it.

Legend points awarded by your game master are claimed in the tab **Campaign**, see below.

!!! example "Screenshot: `player-legend.png`"
    Tab **Legend** with earned and spent entries.

### Notes

The tab **Notes** holds any number of documents for this character, for example a background story or session notes.

- **New** creates a document. The **Document name** may contain letters, digits, spaces and `. _ - ( ) , ! & ' +`.
- Rename and delete a document with the icons next to it (tooltips **Rename** and **Delete**).
- The editor saves automatically and shows **Saved …**.
- The toolbar formats text: headings, **Bold**, **Italic**, **Bullet list**, **Numbered list**. **Insert image** adds a picture at the cursor. **Insert jump mark** adds a link to a heading of the same document.
- Switch between **Edit** and **Preview**. In the preview, links open in a new browser tab and jump marks scroll to the heading.

!!! example "Screenshot: `player-notes.png`"
    Tab **Notes** with a document in the editor and the toolbar.

## Joining a campaign

Your game master invites you by email.

1. Open the link in the invitation email. Sign in if needed.
2. The page **Campaign invitation** shows *You have been invited*, the **Campaign** and **Valid until**.
3. Choose the character that joins the campaign under **Select character**. If you have no character yet, create one first.
4. Click **Accept**. The app confirms *Invitation accepted – welcome to the campaign!*. **Decline** rejects the invitation.

!!! example "Screenshot: `player-invitation.png`"
    Page **Campaign invitation** with character selection.

## The Campaign tab

Once your character belongs to a campaign, the tab **Campaign** appears. A number on the tab shows new messages and documents, and the app plays a sound when something new arrives.

- **Campaign:** name, **Real start date**, **My status** (**Active** or **Inactive**) and the other characters under **Fellow travelers:**.
- **Legend Points:** legend points awarded by the game master. Click **Claim** to take them over. Claimed awards show **Already claimed**.
- **Announcements:** messages from the game master to all players.
- **Chat with GM:** your private chat with the game master. Type under *Write a message...* and click **Send**.
- **Documents from GM:** handouts and documents the game master has shared with you.
- **Leave campaign:** after confirming, you are marked as inactive in the campaign.

!!! example "Screenshot: `player-campaign.png`"
    Tab **Campaign** with legend points, announcements and chat.
