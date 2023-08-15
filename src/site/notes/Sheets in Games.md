---
{"dg-publish":true,"permalink":"/sheets-in-games/"}
---

Related: #programming 
Contents: [[CGRA251 MOC\|CGRA251 MOC]]
[CGRA Lecture Schedule](https://ecs.wgtn.ac.nz/Courses/CGRA251_2023T2/LectureSchedule)
[[UNI MOC\|UNI MOC]]
Hamish Burke || 03-07-2023
***

# Sheets

- Godot sheets (plugin)
- Acts as dictionary
- Define multiple properties of similar types

## Example Uses

- Translation table
	- Key = 'title_name' 
	- Each field diff language

# How to Use

```gdscript
func set_data():
	var cars = GDSheets.sheet("Cars")

	# Get name field from 'fast car 1' object
	$Car1Name.text = cars["Fast Car 1"]["Name"]

func set_title(language:String):
	var translations = GDSheets.sheet("translations")
	$TitleLabel.text = translations["title_nam"][language]
```

# Google Sheets

- Can use Google API to use google sheets

