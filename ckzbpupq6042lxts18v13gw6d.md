## Regular Expressions

Regular Expressions come in handy many times, be it for checking valid Email Id or for matching URLs. This blog comes with a [cheat sheet](https://madhushree-kunder.notion.site/5af80448d1784665a28b7e92d25e7dd6?v=e7ba5207ffa4428a925d6d6a385dc106) to understand regex. 


# Setup

1. Open your favourite code editor and open the search tool.
2. Now turn on the `.*`(regex) and `Aa`(match case)
Like this: 

![search tool bar.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632977966049/A1LuHnWDU.jpeg)

# Literal Characters

So first let's search for literal characters.

![literal char.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632981788737/A0QkxB48S.jpeg)

Only the lowercase `abc` gets matched here and not the uppercase ones. This is because the match case is on. In the image below, you can see that it only matches uppercase ABC.


![caps ABC.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632982656805/lAGSX_IFq.jpeg)

The order in which we write these characters is also important e.g. if we type `bac` it doesn't match `abc`.


![bac.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632982845756/BAAMcazUc.jpeg)

# Meta Characters

![meta characters.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632984191412/4QG_07CN0E.jpeg)

The highlighted characters are known as metacharacters and they need to be escaped.

## Literal . (dot) and \ (backslash)

So what happens when we simply type the special character itself, without escaping it? Let's see :

![all characters.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1632999759069/vONKnzZhK_.jpeg)

*(The search toolbar is on the top left corner with `.` in its search box.) *It matches with every character in the text area, and that is because the dot `.` is a special character in regular expressions. To search for a literal dot `.`, we need to escape it with a backslash `\`. 

![literal dot.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633069402874/tcwWs-rmu.jpeg) 


> So we have learnt that to match special characters, we need to escape them with a backslash `\`. Special characters include: `.[{()\^$|?*+ `

Now let us write a very simple regex to match the literal URL neog.camp, so according to the above statement, the `.` needs to be escaped. 

![neog.camp.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633071887612/HgDlHk1Ws.jpeg)

What we have done here is simply typed the URL itself (and escaped the special character), but in real-world scenarios, we could be writing regular expressions to search for patterns. For that case, we need to write a more generic regular expression which will include using some meta-characters.

Let us take a look at the table below:

![1-1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633106072173/ggNyK1hKS.jpeg)

1. The `.` matches all the characters except a new line as we saw here: 

![all characters.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633106887784/bfEZTLK66.jpeg)

2. `\d` matches with all the digits from 0-9.

![digits.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633107146913/nYJ0c7ey2.jpeg)

3. `\D` matches with everything that is not a digit (0-9).

![not a digit.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633107380803/Zei5fMVXY.jpeg)

> When we search with a `\` along with an uppercase letter, it does the opposite of what the lower case letter search does.  

4. `\w` matches with all the word characters along with underscore. ( a-z, A-Z, 0-9, _ )

![word character.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633110011864/Dc9naW2_b.jpeg)

5. `\W` matches with non-word characters like spaces, punctuation marks and meta characters.

![Not word character.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633110260695/7Pm75U1Nn.jpeg)

6. `\s` matches with whitespace, ie. (space, tab, newline)

![white space all.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633111363956/w8eyCjsCZ.jpeg)

7.  `\S` matches with everything that is not whitespace.

![not whitespace.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633111972725/mepzPmiSI.jpeg)

## Anchors

![anchors.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633112301874/8aCJPjYET.jpeg)

> Anchors don't match any characters, but rather they match invisible positions before and after characters.

1. `\b` word boundary
![word boundary.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633114728936/LOmlkw1fA.jpeg)

We have searched for word boundary `\b` with **to**. The **'to'** in tokyo got matched because there is a word boundary there at the start of the line. For the second **'to'** the space before the word acts as a word boundary. The last 'to' in kyoto does not get matched because there is no word boundary before it. 

![to no word boundary.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633115432939/RCU8N_Esv.jpeg)
In the image above, we have removed the word boundary and simply searched for **'to'** due to which all 3 to's match.

2. `\B` no word boundary

![no word bndry.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633196404903/BberlRhzG.jpeg)

` \B ` matches when there is no word boundary. So, the **'to'** in kyoto gets matched as it has no word boundary before it.  

Let's try wrapping **'to'** in a word boundary(`\bto\b`). Guess what will be the output before reading ahead! 
  
🥁🥁🥁

![b to b.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633197631313/0au2c6F0Y.jpeg)
Only the middle to gets matched because it has word boundary before and after it as well.

3. `^` The caret symbol `^` matches the position at the beginning of a string. Like:

![string char.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633198999664/PQS0oc3J0.jpeg)

4. `$` The dollar symbol matches the position at the end of the string.


![end at the string.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633199158399/-p5Ccgt97.jpeg)

Now let us see some practical examples. We will start by writing some regular expressions for matching some Indian as well as international phone numbers. 

> For phone numbers, we can't type in a literal search as we did before because all the numbers are different. They have a similar pattern but they all have different digits. So in this case we need to use metacharacters instead of literal characters.

### Example-
*International Phone Numbers:*

```
 123-234-9809 & 321.546.9930 
```
We have a pattern here of `3 digits`, and then a `-` (dash) or a `.` (period) followed by 3 more digits and then a `-` (dash) or a `.` (period) and then 4 digits at the end.

> In the  [cheat sheet](https://www.notion.so/5af80448d1784665a28b7e92d25e7dd6?v=e7ba5207ffa4428a925d6d6a385dc106) we can see that we can match a digit using `\d`.


![digit1.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633272704496/lZcqOCvP8.jpeg)
`\d` matches all of the digits as we can see in the image above. 

Now let's start by typing `\d` thrice which will match any 3 digits in a row.

![3 digits.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633276230845/8zxW9AumK.jpeg)

After matching the first 3 digits, we now need to match the `-` dash and `.` in the pattern. For now, let's match any character in the position followed by the first 3 digits. Guess what should we type in to match any character 🤔?? Yep, as we have already learnt, it is a `.` (period/dot).

![ph no. dash dot.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633281686586/FlZlcXfIg.jpeg)
Now let us add the next 3 digits, and it should be simple.


![ph no. 2nd batch.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633282114622/tt86ViLME.jpeg)

We have matched the first 6 digits and the 1st separator (`.`/`-`) in the phone number series, now we need to match the remaining 4 digits and the 2nd separator(`.`/`-`). 

![complete phone number.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633282346544/PXGfG4Ek-.jpeg)
As we can see the regular expression matches all 4 of our phone numbers. 
<br>
Let's take a look at a more realistic example: 
![ph no. db.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633284134002/bQB_xa226.jpeg) 
Here we can see how the regex we wrote comes in handy while searching for phone numbers in a database of information instead of a literal search.
<br> Now let's be a bit more specific about the separator. Currently, our regex matches with any separator even `*` or anything else. But the numbers with such separators are not valid, so we need to rewrite our regex. As you can see in the image below:

![ph no. hash.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633287614800/joa_EJYn9.jpeg) 
To only match a `-` dash or a `.` dot, we need to use a `[ ]` character set. And inside the character set add the characters which are required. In our case, it is obvious that `-` and `.` will be added.

![ph no. only dash dot.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633330723007/PQkzf_h39.jpeg)
Now that we replaced `.` with `[-.]` the regular expression matches only the first two phone numbers.

> Inside the character set, you don't need to escape the `.` character.

Let's say we want to match phone numbers starting with 800 or 900, then our regular expression will change as follows:

![ph no. 8 or 9.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1633331272085/TijnrWwsc.jpeg)

By now we know that `\d` matches with every digit from 0-9. What if we need to match digits only in a particular range, say 2 to 8? For that, we can use a `[ ]` (character set). 
Instead of trying to match `[2345678]`, we can write `[2-8]` and it will match all digits between 2 and 8 (2 and 8 included).

![range of numbers.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644170843481/-Y_jlkYGf.png)

Like digits, the same could be done for alphabets. Say if you want to match only lower case alphabets from 'a' to 'z' you can write `[a-z]` 

![range of alphabets.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644171140828/en_PW6DIa.png)

In the above example, the uppercase alphabets don't get matched. To match both lower and uppercase, we can simply add the uppercase range, i.e `[a-zA-Z]`

![lower and uppercase.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644172309401/clQ-Qm0uQ.png)

To match more characters for e.g. digits, we can write `[a-zA-Z0-9]` 

## ^ inside [ ] 

We know that outside of the character set `[ ]`, `^` matches the beginning of a string. But, within the character set, it negates the set and matches everything that is not in the set. 

Let us look at an example. Say we want to match every character except lower case a-z, then we can write it inside the `[ ]` like `[^a-z]`.

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644176099555/9c7-jGXr7.png)

We can see that here it matches everything that is not a lowercase letter.

Another example would be; say we want to match the words that end with 'at' except the word bat. So we can do this by putting b inside the character set, `[ ]` preceded by `^`. 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644176610020/csex7kJg6.png)

# Quantifiers

## `{ }` 
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644176739866/pZ4Yc4yV5v.png)

Let's take the previous example again. The one with the phone numbers. To match the phone numbers we can write, `\d\d\d.\d\d\d.\d\d\d\d` (`\d` is for matching digit and `.` for matching any separator.)

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644177326891/48BPEHhuj.png)

Notice how we are repeating `\d`, instead, we can use quantifiers. So to match digits, we write: `\d{3}.\d{3}.\d{4}`

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644177468430/epl8G266N.png)

Much cleaner, isn't it? What the `{3}` does is, it matches exactly 3 (digits in our case). Here we are matching exact numbers, but sometimes we don't know the exact number and we may need to use one of these `* + ?` quantifiers.

## `* + ?`

```
Mr. Sharma
Mr Smith
Ms Devi
Mrs. Brown
Mr. J
```

Let us try to write regex for the above names.
First, let's write Regex for names starting with Mr

So we can write `Mr`

![Mr.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1624428346119/mifUrOtWr.jpeg)
Now some names have a dot after the initials. So we need to write a regex to check the dot.

![2.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1624431158222/V3lD-PfMx.jpeg)

The `\.` checks if there is a dot after Mr and the `?` is for allowing either 1 dot or 0 dot. ie. It checks if there is a dot, but allows to match even if there is no dot present.

Now to match the space after Mr, Mr.,  we write `\s` 

![3.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1624431595045/CkKs2rhzB.jpeg)

In the names that are provided, every name starts with a capital letter. So we need to write regex for that.

![4.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1624431936634/Ly_dJBKf0.jpeg)

`[A-Z]` checks for any uppercase letter 

![5.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1624433015643/v6fY6JYTF.jpeg)

`\w` checks for any word character `a-z`, `A-Z`, `0-9`, `_`. But we want to match the characters after the second letter as well right? Can you guess how can we do that? 

 ![think](https://media.giphy.com/media/a5viI92PAF89q/giphy.gif) 

We can put an `*` quantifier which allows matching of 0 or more instances. As we can see the final regex we have written so far is
`Mr\.?\s[A-Z]\w*` but it does not match for Ms, or Mrs. so let's try to incorporate those as well.

What we need is a group `( )` containing cases: After M the possible letters that are mentioned in the question are r, s and rs. So, our group will be `(r|s|rs)`. Notice the `|` means either or-- either `r` or `s` or `rs`. The final regex will look like this:

![7.jpg](https://cdn.hashnode.com/res/hashnode/image/upload/v1624438202014/CX17A5EVI.jpeg)

## Matching Emails

Example: 
```
NeoGCamp@gmail.com
neog.camp@bootcamp.edu
neog-roc8@my-work.net
```
*These are fake email addresses.* But let's try to write a regular expression that will match all of these emails.

*Coming soon...
*





















