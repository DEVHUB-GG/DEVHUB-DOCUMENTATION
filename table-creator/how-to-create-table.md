# ❓ How to create table



{% stepper %}
{% step %}
### Table settings

* Select the table UID; this will be useful later for triggering the event to open the correct table.
* Choose the table prop (it will automatically update after pressing confirm).
* If you have our script on SkillTree, you can enable XP gain after a successful craft.
{% endstep %}

{% step %}
**Rewards**

* You can specify which items the player should have after a successful craft.
{% endstep %}

{% step %}
Needed **items**

* You can specify which items the player must have in their inventory to start crafting.
{% endstep %}

{% step %}
### Props

### **1. Setting the Prop’s Initial Position**

Define the starting position where the prop will first appear in the game world.

### **2. Setting the Prop’s Final Position**

Specify the destination to which the player must move the prop. This marks the end location the prop should be transferred to.

### **3. Configuring Particles (Optional)**

You can enhance the prop with particle effects and sound effects.

* **Particle Settings (Optional):**
  * Set the particle library and particle name.
  * Adjust the particle scale (Optional).
  * If no particle effect is needed but other options are required, leave these fields empty.
* **Sound Settings (Optional):**
  * Provide a URL for the sound effect.
  * If no sound effect is needed, leave this field empty.
  * (The framework used for sound can be modified here.)
* **Additional Particle Properties:**
  * Define the duration for which the particle effect should last.
  * Choose whether the prop should be deleted after the animation finishes (1 = Yes, 0 = No).

***

### **4. Additional Prop Features**

Each prop can be customized with different functionalities:

1. **Static Prop** – The prop remains stationary and cannot be moved.
2. **Spawn Delay** – The prop appears with a delay, becoming visible only when its turn comes.
3. **Model Change** – The prop's model and location can be altered at a specific step (e.g., changing a pot’s appearance when water is poured into it during step 5).

These settings allow you to create a more dynamic and interactive experience using our table.




{% endstep %}
{% endstepper %}
