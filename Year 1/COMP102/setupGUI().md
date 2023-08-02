# setupGUI()

```java
public void setupGUI(){
	UI.initialise();
	UI.setMouseListener(this::doMouse);
	UI.addButton("Quit", UI::quit );
	UI.setFontSize(36);
	UI.quit();
}
```