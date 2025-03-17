Coroutines
Coroutines are used to delay something in a game. Example: when racing, you could set a timer for delaying the message " start race"
To use coroutines use:
```
IEnumerator ExecuteSomething()
{
	yield return new WaitForSeconds(2)
	Debug.Log("hello gamedeveloper, start race");
}
```

The value passed to the ``yield return new WaitForSeconds(VALUE)`` can be a float or integer
Using dynamic or argument
```
IEnumerator ExecuteSomething(int value)
{
	yield return new WaitForSeconds(value)

	Debug.log("Hello gamedeveloper");
}
```
you can have multiple yields :


### **classes**
the sytnax for delcaring classes is:
```
accessModifier class NameOfClass
{

}
```

the accessModifier are private, public, protected
```
public class Player
{
	Debug.Log("Hi am new class == Player"); 
}
```

You need to add a constructor
the constructor should have the same name as that of the class. in inheritance the base class is always required to have a constructor.
## **access modifiers**
public == variables, functions that can be accessed by any class
private == variables, functions that can only be accessed within the class thy're defined
protected
**accessing private variables**

```
public getHealth()
{
	return health // health is a private variable
}
```

**accessibility modfiers**
getters and setters
in getters and setters we use variables previously we used a function to access private variables
```
public class Player
{
	private int _health;
	public int Health;
	{
		get {
			return _health;
		}
	set {
		_health = value;
		}
	}
}
// in my main.cs file:
Player warrior = new Player;
Debug.Log(warrior.Health);
```
## Inheritance
accessing variables and functions from another class
when inheriting from the base class a requirement for the base class is to have a constructor
Example:
player.cs file
```
public class Player
{
	public void Player {} // the constructor can be empty
}
```

main.cs file
Syntax for inheritance : ``AccessModifier class ChildClassName : ParentClassName`` 
```
public class Warrior : Player
{

}
```

in c# constructors are not inherited
In Unity `MonoBehaviour` classes  cannot have constructors with parameters
Instead of using a constructor, **use an `Initialize` method** or set the properties manually.
You cannot use ``new Player()`` because Player is a MonoBehaviour. Instead, use A``ddComponent<Player>()``.

```
GameObject enemyObject = new GameObject("Enemy");
Player enemy_1 = enemyObject.AddComponent<Player>();


GameObject warriorObject = new GameObject("Warrior");
Player Warrior = warriorObject.AddComponent<Player>();

GameObject dragonLordObject = new GameObject("dragonLord");
Player dragonLord = dragonLordObject.AddComponent<Player>();
```

  

in Player.cs instread of using a constructor use an ``Initialize()`` function
```
public class Player ; MonoBehavior
{
	public int health;	
	public int power;
	public string userName;
	public void Initialize(string playerName, int playerHealth, int playerPower)
	{
		this.health = playerHealth;
		this.power = playerPower;
		this.userName = playerName;
	}
}
```

In MonoBehavior classes we do not use ``new ClassName()`` but use ``AddComponent<ClassName>()``



### **override existing functions**
```
using UnityEngine;

  

public class PrinceInheritance : Player

{

public override void Attack()

{

Debug.Log("i attacked with the Dragon sword");

}

}
```



```
public virtual void Attack()
{
	Debug.Log("The " + username + " is attacking");
	Debug.Log("For each Attack the health is reduced by 10 === "+ (health - 10));
}
```

