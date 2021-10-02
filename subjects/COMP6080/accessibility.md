# Lab 04 - Exercise 2

## Performance

Performance relates to accessibility as a service such as Dymocks wants to be available to as wide an audience as possible, and this wide audience could be using any device or live anywhere. 

Older devices and areas of lower internet speeds/coverage would therefore suffer from an inefficient website as load times would suffer the highest to those visitors. 

### Resources

#### Image Format

JPEG image format is used which is inefficient and can be compressed further by using progressive web formats such as JEPG 2000, JPEG XR and WebP which dramatically decrease the file sizes and improve load times. 

#### Lazy Loading

Images that are hidden are unnecessarily loaded in added extra load time, these can be lazily loaded in as they are required.

### Processing

#### Main Thread Code Splitting

8.3 seconds were spent evaluating scripts. This bloated the main thread and severely increased time to interactive. Smaller js payloads can be used to only request resources and run code as it is needed. This can be achieved to a great extent by using the `.then()` method to only run code as something specific has finished running/loading/rendering.

## Accessibility

Specifically accessibility refers to aspects of web dev which make a site able to be used by as many people as possible with as little discrimination or hindrance in usage as possible.

### ARIA (Accessible rich internet applications)

ARIA values give information which can be used by technologies such as screen read. 

In the Dymocks site, some elements have been hidden from aria which decreases accessibility as a screen reader would not narrate those elements.

Some aria attributes also have invalid inputs which cannot be interpreted and are therefore useless.

Both these instances hide information from people with vision impairments for example. 

### Image Alt

Images within the page do not have alt text. If the load becomes unexpectedly poor the page can at least display alt text usually in order to convey some information. Screen readers can also use alt text to narrate images which cannot happen in these cases anymore. 

## Code and Visual Analysis

### Nesting

Everything except popups is nested within one form tag, and there are also many hidden input tags which seems an unnecessary method. 

### Responsiveness

The site has 3 breakpoints for responsive design at 1200px, 990px and 768px. The carousel layout is bugged from widths below 990px. 3 breakpoints are good for catering to various devices, however their below 990px layout minor adjustments.

### Colours

The Bestsellers section has very low colour contrast between the yellow background and white text which makes it difficult to read for a visually impaired person. 