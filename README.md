# ConvertKindleBookToPdf
Way to convert kindle book to pdf

## Information provided below is just for informational purpose. Don’t use it for illegal purposes.

Basic Idea used in this is that we can do following things using command line 
1. Take a screenshot of a page (using scrot for linux and screenshot for mac).
2. Mouse click (using xdotool works both in linux and mac)
3. Convert pictures to pdf (using convert)

### Taking a screenshot

**On Linux**
```bash
scrot abc.png
```

**On Mac**
```bash
screenshot abc.png
```

### Mouse click
**On linux and mac**
```bash
xdotool click 1
```

### Convert images to pdf
```bash
convert image1.jpg image2.png output.pdf
```

#### Automate taking pics using screenshot and mouse click using bash
```bash
#!/bin/bash
sleep 5
while :
do
echo “Press [CTRL+C] to stop..”
((var=var+1))
sleep 0.05
scrot $var.png
xdotool click 1
done
```

So after running this script make sure your mouse is pointing to the next button of your kindle cloud reader book next button. After that button click can be automated automatically by this script. **Make sure to press Ctrl+C after last page as this script can not identify if all pages are completed or not**


Now we need some library that can convert these pictures to pdf. In linux again we can do this using convert. So created pictures can be converted to pdf using this script
#### Convert images to pdf
```bash
#!/bin/bash
file=$1
convert `ls -1v | grep png` $file.pdf
rm *png
```
