# Content
* [Overview](#overview)
* [C# Code Standards](#c-code-standards)
* [Rule for Nomenclature of Variables and Methods](#rules-for-naming-variables-properties-and-function)
* [Standard Script Pattern](#standard-script-pattern)
* [Use of Prefabs](#use-prefabs)


# Overview
* Primary goal of having coding conventions is to ensure consistency & clarity in codebase.
* Good coding conventions can help convey Intent and Context clearly for any piece of code in its scope of execution.
* Coding conventions can often be more of recommendations and guidelines than hard and strict rules. As such there can be exception to these conventions. Developer's better judgement should prevail in these situations with the primary goal of conveying intent clearly in codebase.
* A good code is not only efficient but readable too. We would have to trade off between both. Coventions help us make code readable which is very important if we are working in team. 
* In CP, we write code which should just run fast. In Project, we mayhave to check and debug same line of code, refractor multiple times which makes readability a important factor.
* If convention is followed effectively, it will reduce need of comments to make code understandable.

# C# Code Standards
| Object Name | Notation  | Plural | Char Mask |
|--- | --- | ---| ---|
|Struct|PascalCase|No|[A-z][0-9]|
|Class|PascalCase|No|[A-z][0-9]|
|Method|PascalCase|Yes|[A-z][0-9]|
|Enum type|PascalCase|Yes|[A-z]|
|Static Variable|camelCase|Yes|[A-z][0-9]|
|Public Field|camelCase|Yes|[A-z][0-9]|
|Private Field|m_camelCase|Yes|[A-z][0-9]|
|Method Argument|a_camelCase|Yes|[A-z][0-9]|
|Property|PascalCase|Yes|[A-z][0-9]|
|Constant|CAPITAL_CASE|No|[A-z][0-9]|


# Rules for naming Variables, Properties and Function
* ### Prefer use of full words for variables names unless running into very long names. Names should carry intent of use. e.g.,
    #### Use this
    ```csharp
    Vector3 playerPosition;
    ```
    #### Over this
    ```csharp
    Vector3 playerPos; 
    ```

* ### Prefer use of plural words for names of Array/List names.
    #### Example
    ```csharp
    GameObject[] barriers;
    List<Car> cars;
    ```

* ### Prefer use of interrogative names for booleans. 
    #### Example
    ```csharp
    bool isJumping;
    ```



# Standard Script Pattern
* ### Codes should be separated in regions, e.g.,fields,methods,etc.
* ### Variables, properties or fuctions should be declared according to scope in order: public->private.
* ### Serializable fields should be declared above non-serializable in that scope.
* ### All static fields should be declared above non-static.
* ### All the members of a script should be organized in following order
    1. Public Sub-Types
    1. Private Sub-Types
    1. Static Fields
    1. Public Fields
    1. Private Fields
    1. Public Properties
    1. Private Properties //generally uncommon
    1. Unity callbacks
    1. Public Methods
    1. Private Methods

```csharp
using UnityEngine;

namespace XYZ
{
    public class Player : Monobehaviour
    {
        #region Sub-Types
        public struct PlayerData { }
        #endregion

        #region Fields
        public PlayerData playerData
        private int m_health;
        #endregion

        #region Properties
        public int Health 
        {
            get { return m_health; }
            set 
            {
                if (value > 100) m_health = 100;
                else if (value < 0) m_health = 0;
                else m_health = value;
            }
        }
        #endregion

        #region Unity-Callbacks
        private void Awake() { }
        private void Start() { }
        private void Update() { }
        private void FixedUpdate() { }
        private void OnCollissionEnter() { }
        #endregion

        #region Methods
        public void Attack(GameObject a_enemy) { }
        private void Move() { }
        #endregion
    }
}
```

# Use Prefabs
* Why? 
    * We can make scene hierarchy modular. i.e., we can change any specific part of environment and we also don't need to commit complete scene. 
    * This will reduce merge conflicts on scene.
    * Prefabs can be easily exported and used in other games.
* Always Use Prefabs as gameobjects and use scene as a container only.
* Use Prefabs to combine and make higher level prefab in hierarchy. i.e., Nest Prefabs.
* Read [this documentation](https://docs.unity3d.com/Manual/Prefabs.html) to get detailed idea of different stages of Prefabs. i.e., Overrides, Variants, etc.
* Always do serialization inside prefabs. Never do it in scene.
* Now, you will face a problem that how to serialize objects which are not part of prefab but will be part of scene. For example, Score calculating script wants to show GameOver Panel on win/lose. Earlier we could have serialized GameOver panel to score script. (Which is completely wrong and should not be done even if we were not using prefabs as score calculating script should not have direct reference to UI elements beacuse these type of referencing makes code hard to debug. Score script should have reference to any UI manager which is handling all UI related stuffs.). Now lets make situation clear that we want to link two scripts/object together and both are just instantiated and one have no idea of where other is (slightly dramatic). This can be solved in several ways:
    * Find() : find the object you want by Find or FindWithTag functions and you will get your object which you want to reference. Although this will work, it should not be used as it iterates for each object in scene and is computationally expensive. Warning! never use in update loop.
    * Singleton : Read [this](https://www.dofactory.com/net/singleton-design-pattern) to know about singleton pattern. A singleton instance can be accessed using its static variable referencing to itself. When both the objects are instantiated, they can reference themselves to this singleton instance. Now this reference can be used wherever we want. This also has drawback that it makes code harder to debug.
    * There are more efficient ways which we will discuss in future.

<!-- 
# Use Scriptable Objects 
-->