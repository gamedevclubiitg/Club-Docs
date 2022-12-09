# Overview
* Primary goal of having coding conventions is to ensure consistency & clarity in codebase.
* Good coding conventions can help convey Intent and Context clearly for any piece of code in its scope of execution.
* Coding conventions can often be more of recommendations and guidelines than hard and strict rules. As such there can be exception to these conventions. Developer's better judgement should prevail in these situations with the primary goal of conveying intent clearly in codebase.

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