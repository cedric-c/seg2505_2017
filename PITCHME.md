### Développement d'applications Android

Laboratoire Android 2 : Les menus, les interactions et les activités

<span style="color:gray"></span>

<span style="color:gray">SEG 2505 - Introduction au génie logiciel</span>

<span style="color:gray">Automne 2017</span>

<span style="color:gray">Présenté par : Cédric Clément</span>

---

#### Plan

1. Éléments d'interfaces usagers
2. Les activités
3. Les intentions
4. Le transfert de données
5. Travail de laboratoire

<span style="font-size:0.6em;color:gray">Appuyez sur la clé <span style="color:#3884b9">**O**</span> pour voir un survole de la présentation.</span>

---

#### Éléments d'interfaces usagers

+++

##### Menus et la barre d'action

- <span style="font-size:0.6em;color:gray">Android vous offre une variété d'éléments visuels</span>
    - <span style="font-size:0.6em;color:gray">options dans les <span style="color:#00aa60">menus</span></span>
    - <span style="font-size:0.6em;color:gray"><span style="color:#e8bf6a">barre</span> d'action</span>
    - <span style="font-size:0.6em;color:gray">menu contextuel ("long-click")</span>
    - <span style="font-size:0.6em;color:gray">"<span style="color:#3884b9">popup</span>"</span>
- <span style="font-size:0.6em;color:gray">définitions de ces éléments en <span style="color:#d0d0ff">XML</span></span>

Note:
- Menu "Popup" : les actions dans ces menus ne devraient pas avoir un impacte directe sur le contenu, mais plutôt pour les séries d'actions

+++

<span style="color:gray">La gestion de ces événements se fait avec des "<span style="color:#3884b9">Click Events</span>" comme <span style="color:white">`OnClick()`</span> ou avec un <span style="color:#c45331">Override</span> de <span style="color:white">`onOptionItemSelected()`</span>.</span>

+++

#### Les fragments

- <span style="font-size:0.6em;color:gray">représentente des <span style="color:#00aa60">portions</span> d'une interface</span>
- <span style="font-size:0.6em;color:gray">peuvent être <span style="color:#e8bf6a">combinés</span></span>
- <span style="font-size:0.6em;color:gray"><span style="color:#3884b9">modulaire</span></span>

![assets](assets/resized/slides/100/image11.png)

Note:
- les Fragments sont utilisés pour représenter des portions d'une interface d'utilisateur
- plusieurs Fragments peuvent être combinés pour créer une interface
- les Fragments sont réutilisables et modulaires

+++

#### Tiroire de navigation

<span style="font-size:0.6em;color:gray">Panneau qui présente les <span style="color:#b4c973">fonctions de navigation</span> pour l'application.</span>

<span style="font-size:0.6em;color:gray">Types:</span>
1. <span style="font-size:0.6em;color:gray">**Permanent**: <span style="color:#a1617a">toujours présent</span></span>
2. <span style="font-size:0.6em;color:gray">**Persistant**: ouvrir/fermer/basculer, <span style="color:#00aa60">déplace</span> le contenu</span>
3. <span style="font-size:0.6em;color:gray">**Temporaire**: ouvrir/fermer/basculer, <span style="color:#d0d0ff">masque</span> le contenu</span>
4. <span style="font-size:0.6em;color:gray">**Mini-Variable**: petit panneau avec des <span style="color:orange">icônes seulement</span>. Peut être utilisé dans l'état fermé.</span>

Note:
- C'est un panneau qui présente les fonctions de navigation pour l'application. Il y a 4 types:
1. Permanent: toujours présent
2. Persistant: ouvrir/fermer/basculer, déplace le contenu
3. Temporaire: ouvrir/fermer/basculer, masque le contenu
4. Mini-Variable: petit panneau avec des icônes seulement. Peut être utilisé dans l'état fermé.

+++

![assets](assets/resized/slides/50/image16.png)

+++

#### Les dialogues

- invitent l'utilisateur à <span style="color:#e8bf6a">prendre une décision</span>
- types: `AlertDialog`, `DatePickerDialog`, `TimePickerDialog`, `Custom`

![dialog](assets/resized/slides/100/image17.png)


Note:
- les dialogues invitent l'utilisateur à prendre/fournir une décision ou pour des informations supplémentaires avant que l'application peut continuer
- types de dialogues
- AlertDialog
- DatePickerDialog
- TimePickerDialog
- Custom Layout

---

### Les activités

---

### Les intentions

---

### Le transfert de données

---

### Travail de laboratoire


---





### Example de code

```java
import android.os.Bundle;
import android.app.Activity;
import android.view.Menu;
import android.view.View;
import android.widget.EditText;

public class MainActivity extends Activity {
    private enum Operator {none, add, minus, multiply, divide};
    private double data1 = 0, data2 = 0;
    private Operator optr = Operator.none;
    
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    
    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if present
        getMenuInflater().inflate(R.menu.main, menu);
        return true;
    }
    
    public void btn00Click(View view) {
        EditText eText = (EditText) findViewById(R.id.resultEdit);
        eText.setText(eText.getText() + "0");
    }
    
}

```

@[1-5](imports)
@[8-10](nous avons ajouté ces variables)
@[12-22](cette portion du code est générée automatiquement)

<!-- ### Calculatrice simple : exemple de code 1 -->
<!--  -->
<!-- Nous avons ajouté ces variables -->
<!-- Cette portion du code est générée automatiquement -->

+++

```java
// MainActivity.java

public void btn01Click(View view) {
    EditText eText = (EditText) findViewById(R.id.resultEdit);
    eText.setText(eText.getText() + "1");
}

public void btn02Click(View view) {
    EditText eText = (EditText) findViewById(R.id.resultEdit);
    eText.setText(eText.getText() + "2");
}

// ...

public void btnAddClick(View view) {
    optr = Operator.add;
    EditText eText = (EditText) findViewById(R.id.resultEdit);
}

public void btnMinusClick(View view) {
    optr = Operator.minus;
    EditText eText = (EditText) findViewById(R.id.resultEdit);
    data1 = Double.parseDouble(eText.getText().toString());
    eText.setText("");
}

public void btnMultiplyClick(View view){
    optr = Operator.multiply;
    EditText eText = (EditText) findViewById(R.id.resultEdit);
    data1 = Double.parseDouble(eText.getText().toString());
    eText.setText("");
}

public void btnDivideClick(View view){
    optr = Operator.divide;
    EditText eText = (EditText) findViewById(R.id.resultEdit);
    data1 = Double.parseDouble(eText.getText().toString());
    eText.setText("");
}

public void btnClearClick(View view){
    EditText eText = (EditText) findViewById(R.id.resultEdit);
    eText.setText("");
}

public void btnDotClick(View view){
    EditText eText = (EditText) findViewById(R.id.resultEdit);
    eText.setText(eText.getText() + ".");
}

public void btnResultClick(View view) {
    if(optr != Operator.none){
        EditText eText = (EditText) findViewById(R.id.resultEdit);
        data2 = Double.parseDouble(eText.getText().toString());
        double result = 0;
        if(optr == Operator.add) {
            result = data1 + data2;
        } else if (optr == Operator.minus) {
            result = data1 - data2;
        } else if (optr == Operator.multiply) {
            result = data1 * data2;
        } else if (optr == Operator.divide) {
            result = data1 / data2;
        }
        optr = Operator.none;
        data1 = result;
        if((result - (int) result) != 0)
            eText.setText( String.valueOf(result) );
        else
            eText.setText( String.valueOf( (int) result ) );
    }
}

public void onClickNumericalButton (View view) {
    int pressID = view.getId();

    TextView curText = (TextView) findViewById(R.id.resultEdit);

    switch (pressID) {
        case R.id.btn00:
            curText.setText(curText.getText() + "0");
            break;
        case R.id.btn01:
            curText.setText(curText.getText() + "1");
            break;
        case R.id.btn02:
            curText.setText(curText.getText() + "2");
            break;
        case R.id.btn03:
            curText.setText(curText.getText() + "3");
            break;
        case R.id.btn04:
            curText.setText(curText.getText() + "4");
            break;
        case R.id.btn05:
            curText.setText(curText.getText() + "5");
            break;
        case R.id.btn06:
            curText.setText(curText.getText() + "6");
            break;
        case R.id.btn07:
            curText.setText(curText.getText() + "7");
            break;
        case R.id.btn08:
            curText.setText(curText.getText() + "8");
            break;
        case R.id.btn09:
            curText.setText(curText.getText() + "9");
            break;
        case R.id.btnDot:
            curText.setText(curText.getText() + ".");
            break;
        default:
            curText.setText("ERROR");
            //Log.d("Error","Error: Unknown Button pressed!");
            break;
    }
}
```
