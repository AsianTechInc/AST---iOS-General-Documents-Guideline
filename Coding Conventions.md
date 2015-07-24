# ASIANTECH INC: iOS Coding Guidlines

<<<<<<< HEAD
This document covers naming and formatting conventions used for iOS application development at AsianTech Inc.

Since this is an Objective-C/Cocoa project, we follow and extend [Apple’s Cocoa Coding Guidelines](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html#//apple_ref/doc/uid/10000146-SW1). Make sure to be familiar with this document.
=======
This document covers naming and formatting conventions used to program AsianTech Inc iOS applications.

Since this is an Objective-C/Cocoa project, we follow and extend [Apple’s Cocoa Coding Guidelines](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/CodingGuidelines.html#//apple_ref/doc/uid/10000146-SW1). Make sure to familiarize yourself with this document.
>>>>>>> 1.0.0

In general, use your best judgement as you write your code. Your goals should be:

 * Readability 
 * Clarity
 * Consistency

---

# Naming Conventions

Follow the naming conventions set by Apple in the [Cocoa Coding Guidelines](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingBasics.html#//apple_ref/doc/uid/20001281-BBCHBFAH). 

### Application Namespace:

Use a prefix that identifies the application (example: ET for an app called EduTower). Use this prefix when naming classes, functions, constants and typedef structures.

### Class Names:

**App prefix + Camel case description**

 * Start class names with the app prefix
 * Class names should be as descriptive as possible, avoid shorthand and abbreviations
 * If subclassing, make it obvious by using the superclasses name in the new name

<table>
  <tr>
		<td><code>ETTableVC</code></td><td>bad</td>
    </tr>
	<tr>
		<td><code>ETTableViewController</code></td><td>good</td>
	</tr>
	<tr>
		<td><code>ETRoomInfoViewController</code></td><td>good</td>
	</tr>	
</table>

## Variables

**Lower-case identifier + Camel case description**

The lower-case identifier prefixes are designed to provide information, or metadata, about the variable. This helps with debugging and general readability by removing any ambiguity about the origin of the variable or the intended use of the variable.

### Instance Variables

Instance variables are auto-synthesized in Objective-C.  By default, the name is comprised of the property name prefixed by an underscore.  

So by declaring the property:

```
@property (nonatomic, strong) NSString *title;
```
you will be creating the instance variable:

```
NSString *_title
```

### Constants
 
**App Prefex**
For public constants

```
extern NSString *const ETOperationFailingURLResponseErrorKey;
```

**'k'**
For constants that are local to a file, use 

```
static CGFloat const kMaxConcurrentOperationCount = 3;
```

### struct names

**App prefix + name**

```
typedef struct
{
	CGFloat red;
	CGFloat green;
	CGFloat blue;
	CGFloat alpha;
	
}ETColor;
```

### Enums

Use the same convention to name the enum as you would structs

**App prefix + name**

For the values:

**Enum name + underscore + name**

```
typedef enum
{
	ETRoomState_Open,
	ETRoomState_Closed
	
}ETRoomState;
```

## Methods and Functions

Method names start with a lower case letter followed by camel casing:

```
- (void)initWithFrame:(NSRect)frame;
- (NSArray*)selectedItems;
```

The Cocoa Coding Guidelines section on naming methods has very good advice for naming Objective-C methods:
[https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-BCIGIJJF](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-BCIGIJJF)

### Functions
Functions start with the App prefix followed by a camel case description:

```
ETDrawStringInRect(theString, theRect);
```
Read the Cocoa Coding Guidelines section on naming functions:
[https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingFunctions.html#//apple_ref/doc/uid/20001283-BAJGGCAD)

### Blocks

Call blocks 'blocks' (as opposed to 'handler' or nothing at all)

<table>
	<tr>
		<td><code>- (NSString *)signInWithCompletionBlock:(ETHTTPRequestCompletionBlock)completionBlock;</code></td><td>good</td>
    </tr>
	<tr>
		<td><code>- (NSString *)signInWithCompletionHandler:(ETHTTPRequestCompletionBlock)theCompletionHandler;</code></td><td>bad</td>
	<tr>
		<td><code>- (NSString *)signInWithCompletion:(ETHTTPRequestCompletionBlock)theCompletionHandler;</code></td><td>bad</td>
</table>


### Delegate Methods + Notification Names

**Class name + behavior being described**

Delegate methods and notification names should use the form "Did", "Will" and "Should"

See Apple's guide on naming delegate methods:
[https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-BCIGIJJF](https://developer.apple.com/library/mac/#documentation/Cocoa/Conceptual/CodingGuidelines/Articles/NamingMethods.html#//apple_ref/doc/uid/20001282-BCIGIJJF)

Delegate methods:

```
- (BOOL)listView:(ETListView *)listView shouldSelectItemAtIndex:(NSInteger)theIndex;
- (void)listView:(ETListView *)listView didSelectItemAtIndex:(NSInteger)theIndex;
- (void)listView:(ETListView *)listView willDisplayItemAtIndex:(NSInteger)theIndex;
```

Notificaiton names:

```
extern NSString *const ETRoomWillCloseNotifcation;
```

## General Naming Guidelines 


###Avoid abbreviations and shorthand

Avoid abbreviations and shorthand when choosing a name. Longer names are often better than shorter names.

<table>
	<tr>
		<td><code>aCol</code></td><td>bad</td>
    </tr>
	<tr>
		<td><code>aColumn</code></td><td>good</td>
	</tr>	
</table>

It is OK to use abbreviations or shorthand in some cases such as:
 * min instead of minimum
 * max instead of maximum
 * i, j to index an array in a for loop
See http://developer.apple.com/DOCUMENTATION/Cocoa/Conceptual/CodingGuidelines/ Articles/APIAbbreviations.html#//apple_ref/doc/uid/20001285 for a list of acceptable abbreviations.

WARNING: Ignore the second bullet point in the Apple document:
 * You may use abbreviations more freely in argument names (for example, “imageRep”, “col” (for
“column”), “obj”, and “otherWin”).

Argument names should be as carefully considered as any other names. See “Method Arguments” for our rules for these types of names. Some of the examples they give are not acceptable (“otherWin”, “obj”).

### Be specific
 
Name methods, variables, and classes so that your intent is clear.
￼￼
<table>
	<tr>
		<td><code>add:</code></td><td>add what?</td>
    </tr>
	<tr>
		<td><code>addName:</code></td><td>good</td>
	</tr>
	<tr>
		<td><code>NSArray *anArray;</code></td><td>an array of what?</td>
    </tr>
	<tr>
		<td><code>NSArray *aNamesToAdd;</code></td><td>very good - we know what is in the list and what the list is for</td>
	</tr>	
</table>

### Be Consistent

As you’re building a code base, try to stay consistent in your naming style and stay consistent with Apple’s conventions as much as you can.

---

#Formatting

Even though each programmer will have his or her own style of programming, it is important to remember that others will need to read, debug and extend the code that you write.  In order to maintain a high-quality and consistent code base, everyone is required to follow the formatting guidelines in this section. 

## Whitespace

### Pointers

Pointers go in front of the variable name with no white space.

<table>
	<tr>
		<td><code>NSString *aTitle</code></td><td>good</td>
    </tr>
	<tr>
		<td><code>NSString* aTitle</code></td><td>bad</td>
	</tr>
	<tr>
		<td><code>NSString * aTitle</code></td><td>bad</td>
    </tr>
</table>

### if/else/for/while

Put a white space between the statement and the parentheses

```
if (theIndex >= 0) {
	// do something
} else {
	// do something else
}

// for (aThing in theThings)
// while (aThing == YES)

```

### Brackets

```
- (void)layoutSubviews 
{
	for (UIView *aView in self.subviews) {
		aView.frame = aFrame;
	}
	
	if (x == 1) {
		// do something
	} else if (x == 2) {
		// do something else
	} else {
		// do something else
	}
}
```

With the exception of blocks inside of a method argument:

```
[UIView animateWithDuration:.25 animations:^ {
    <#code#>
} completion:^(BOOL finished) {
    <#code#>
}];

```
### Indention

Use the default setting in Xcode: 4 spaces
