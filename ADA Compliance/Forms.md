Required text fields
```
<form>
  <p>* required</p>
  <label for="username">Username*:</label>
  <input type="text" id="username" name="username" required/>

  <label for="email">Email*:</label>
  <input type="text" id="email" name="email" required/>

  <input type="submit" value="Submit" />
</form>
```

Radio buttons
```
<fieldset>
  <legend>Options</legend>

  <label for="option1">Option 1</label>
  <input type="radio" name="option1" id="option1" value="option1"/>

  <label for="option2">Option 2</label>
  <input type="radio" name="option2" id="option1" value="option2"/>

</fieldset>
```

Checkbox
```
<fieldset>
  <legend>Options</legend>

  <label for="option1">Option 1</label>
  <input type="checkbox" name="option1" id="option1" value="option1" checked/>

  <label for="option2">Option 2</label>
  <input type="checkbox" name="option2" id="option2" value="option2"/>
</fieldset>
```