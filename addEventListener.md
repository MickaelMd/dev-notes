## Liste des événements JavaScript courants avec addEventListener

### Événements liés à la souris

**click :** Se déclenche lorsqu'un élément est cliqué.

```js

document.getElementById('element').addEventListener('click', function() {
  console.log('Élément cliqué');
});
  
```

**dblclick :** Se déclenche lorsqu'un élément est double-cliqué.

```js

document.getElementById('element').addEventListener('dblclick', function() {
  console.log('Élément double-cliqué');
});
  
```

**mousedown :** Se déclenche lorsque l'utilisateur appuie sur un bouton de la souris.

```js

document.getElementById('element').addEventListener('mousedown', function() {
  console.log('Bouton de la souris enfoncé');
});
  
```

**mouseup :** Se déclenche lorsque l'utilisateur relâche un bouton de la souris.

```js

document.getElementById('element').addEventListener('mouseup', function() {
  console.log('Bouton de la souris relâché');
});
  
```

**mouseenter :** Se déclenche lorsque la souris entre dans un élément.

```js

document.getElementById('element').addEventListener('mouseenter', function() {
  console.log('La souris entre dans l\'élément');
});
  
```

**mouseleave :** Se déclenche lorsque la souris quitte un élément.

```js

document.getElementById('element').addEventListener('mouseleave', function() {
  console.log('La souris quitte l\'élément');
});
  
```

**mousemove :** Se déclenche lorsque la souris se déplace à l'intérieur d'un élément.

```js

document.getElementById('element').addEventListener('mousemove', function() {
  console.log('La souris se déplace dans l\'élément');
});
  
```

**mouseover :** Se déclenche lorsque la souris survole un élément.

```js

document.getElementById('element').addEventListener('mouseover', function() {
  console.log('La souris survole l\'élément');
});
  
```

**mouseout :** Se déclenche lorsque la souris quitte un élément.

```js

document.getElementById('element').addEventListener('mouseout', function() {
  console.log('La souris quitte l\'élément');
});
  
```

### Événements liés au clavier

**keydown :** Se déclenche lorsqu'une touche est enfoncée.

```js

document.addEventListener('keydown', function() {
  console.log('Touche enfoncée');
});
  
```

**keyup :** Se déclenche lorsqu'une touche est relâchée.

```js

document.addEventListener('keyup', function() {
  console.log('Touche relâchée');
});
  
```

**keypress :** Se déclenche lorsqu'une touche est pressée et maintenue enfoncée.

```js

document.addEventListener('keypress', function() {
  console.log('Touche pressée');
});
  
```

### Événements liés au focus

**focus :** Se déclenche lorsqu'un élément reçoit le focus (entrée de texte, par exemple).

```js

document.getElementById('element').addEventListener('focus', function() {
  console.log('L\'élément reçoit le focus');
});
  
```

**blur :** Se déclenche lorsque l'élément perd le focus.

```js

document.getElementById('element').addEventListener('blur', function() {
  console.log('L\'élément perd le focus');
});
  
```

### Événements de formulaire

**submit :** Se déclenche lorsqu'un formulaire est soumis.

```js

document.getElementById('form').addEventListener('submit', function() {
  console.log('Formulaire soumis');
});
  
```

**change :** Se déclenche lorsqu'un élément de formulaire change de valeur.

```js

document.getElementById('input').addEventListener('change', function() {
  console.log('Valeur de l\'élément modifiée');
});
  
```

**input :** Se déclenche chaque fois que l'utilisateur entre des caractères dans un champ de saisie.

```js

document.getElementById('input').addEventListener('input', function() {
  console.log('Entrée de texte');
});
  
```

**focusin :** Se déclenche lorsque l'élément ou l'un de ses enfants reçoit le focus.

```js

document.getElementById('element').addEventListener('focusin', function() {
  console.log('Focus dans l\'élément ou ses enfants');
});
  
```

**focusout :** Se déclenche lorsque l'élément ou l'un de ses enfants perd le focus.

```js

document.getElementById('element').addEventListener('focusout', function() {
  console.log('Focus perdu dans l\'élément ou ses enfants');
});
  
```

### Événements de chargement

**load :** Se déclenche lorsque la page ou un élément (comme une image) a fini de se charger.

```js

window.addEventListener('load', function() {
  console.log('Page chargée');
});
  
```

**DOMContentLoaded :** Se déclenche lorsque le DOM est entièrement chargé.

```js

document.addEventListener('DOMContentLoaded', function() {
  console.log('DOM chargé');
});
  
```

**beforeunload :** Se déclenche avant que la page ne soit déchargée ou fermée.

```js

window.addEventListener('beforeunload', function() {
  console.log('Page va être déchargée');
});
  
```

**unload :** Se déclenche lorsque la page est déchargée.

```js

window.addEventListener('unload', function() {
  console.log('Page déchargée');
});
  
```

### Événements de la fenêtre

**resize :** Se déclenche lorsque la taille de la fenêtre change.

```js

window.addEventListener('resize', function() {
  console.log('Taille de la fenêtre modifiée');
});
  
```

**scroll :** Se déclenche lorsque l'utilisateur fait défiler la page.

```js

window.addEventListener('scroll', function() {
  console.log('Page défilée');
});
  
```

**orientationchange :** Se déclenche lorsque l'orientation de l'appareil change.

```js

window.addEventListener('orientationchange', function() {
  console.log('Orientation de l\'appareil modifiée');
});
  
```

### Événements tactiles

**touchstart :** Se déclenche lorsqu'un doigt touche l'écran.

```js

document.addEventListener('touchstart', function() {
  console.log('Toucher sur l\'écran');
});
  
```

**touchend :** Se déclenche lorsqu'un doigt quitte l'écran.

```js

document.addEventListener('touchend', function() {
  console.log('Doigt quitté l\'écran');
});
  
```

**touchmove :** Se déclenche lorsque le doigt se déplace sur l'écran.

```js

document.addEventListener('touchmove', function() {
  console.log('Doigt déplacé sur l\'écran');
});
  
```

**touchcancel :** Se déclenche lorsqu'une interaction tactile est annulée.

```js

document.addEventListener('touchcancel', function() {
  console.log('Interaction tactile annulée');
});
  
```

### Autres événements divers

**error :** Se déclenche lorsqu'une erreur se produit (par exemple, lors du chargement d'une image).

```js

window.addEventListener('error', function() {
  console.log('Erreur survenue');
});
  
```

**wheel :** Se déclenche lors du défilement avec la molette de la souris.

```js

document.addEventListener('wheel', function() {
  console.log('Molette de la souris utilisée');
});
  
```

**drag :** Se déclenche lorsqu'un élément est déplacé (glissé).

```js

document.addEventListener('drag', function() {
  console.log('Élément déplacé');
});
  
```

**dragstart :** Se déclenche lorsque l'élément commence à être déplacé.

```js

document.addEventListener('dragstart', function() {
  console.log('Déplacement commencé');
});
  
```

**dragend :** Se déclenche lorsque l'élément finit d'être déplacé.

```js

document.addEventListener('dragend', function() {
  console.log('Déplacement terminé');
});
  
```

**drop :** Se déclenche lorsqu'un élément est déposé après avoir été déplacé.

```js

document.addEventListener('drop', function() {
  console.log('Élément déposé');
});
  
```


### Événements réseau

**online :** Se déclenche lorsque l'appareil passe en ligne.

```js

window.addEventListener('online', function() {
  console.log('Appareil en ligne');
});
  
```

**offline :** Se déclenche lorsque l'appareil passe hors ligne.

```js

window.addEventListener('offline', function() {
  console.log('Appareil hors ligne');
});
  
```

### Événements liés aux animations et transitions CSS

**transitionstart :** Se déclenche au début d'une transition CSS.

```js

document.getElementById('element').addEventListener('transitionstart', function() {
  console.log('Transition commencée');
});
  
```

**transitionend :** Se déclenche à la fin d'une transition CSS.

```js

document.getElementById('element').addEventListener('transitionend', function() {
  console.log('Transition terminée');
});
  
```

**animationstart :** Se déclenche au début d'une animation CSS.

```js

document.getElementById('element').addEventListener('animationstart', function() {
  console.log('Animation commencée');
});
  
```

**animationend :** Se déclenche à la fin d'une animation CSS.

```js

document.getElementById('element').addEventListener('animationend', function() {
  console.log('Animation terminée');
});
  
```

**animationiteration :** Se déclenche à chaque itération d'une animation CSS.

```js

document.getElementById('element').addEventListener('animationiteration', function() {
  console.log('Nouvelle itération d\'animation');
});
  
```

### Autres événements divers

**contextmenu :** Se déclenche lorsqu'un utilisateur fait un clic droit pour ouvrir le menu contextuel.

```js

document.getElementById('element').addEventListener('contextmenu', function(e) {
  e.preventDefault(); // Pour désactiver le menu contextuel par défaut
  console.log('Menu contextuel ouvert');
});
  
```

**copy, cut, paste :** Se déclenchent respectivement lors de la copie, la coupe, et le collage de contenu.

```js

document.getElementById('element').addEventListener('copy', function() {
  console.log('Contenu copié');
});

document.getElementById('element').addEventListener('cut', function() {
  console.log('Contenu coupé');
});

document.getElementById('element').addEventListener('paste', function() {
  console.log('Contenu collé');
});
  
```

**visibilitychange :** Se déclenche lorsque la visibilité de la page change (par exemple, lorsqu'un utilisateur change d'onglet).

```js

document.addEventListener('visibilitychange', function() {
  console.log(document.visibilityState);
});
  
```

### Événements liés aux médias

**play :** Se déclenche lorsque la lecture d'un média commence.

```js

document.getElementById('media').addEventListener('play', function() {
  console.log('Lecture commencée');
});
  
```

**pause :** Se déclenche lorsque la lecture d'un média est mise en pause.

```js

document.getElementById('media').addEventListener('pause', function() {
  console.log('Lecture mise en pause');
});
  
```

**ended :** Se déclenche lorsque la lecture d'un média est terminée.

```js

document.getElementById('media').addEventListener('ended', function() {
  console.log('Lecture terminée');
});
  
```

**volumechange :** Se déclenche lorsque le volume d'un média est modifié.

```js

document.getElementById('media').addEventListener('volumechange', function() {
  console.log('Volume changé');
});
  
```

### Événements liés aux éléments personnalisés (Web Components)

**connectedCallback :** Se déclenche lorsqu'un élément personnalisé est ajouté au DOM.

```js

class CustomElement extends HTMLElement {
  connectedCallback() {
    console.log('Élément ajouté au DOM');
  }
}
customElements.define('custom-element', CustomElement);
  
```

**disconnectedCallback :** Se déclenche lorsqu'un élément personnalisé est retiré du DOM.

```js

class CustomElement extends HTMLElement {
  disconnectedCallback() {
    console.log('Élément retiré du DOM');
  }
}
customElements.define('custom-element', CustomElement);
  
```

### Événements de mutation (MutationObserver)

**MutationObserver :** Pour observer des modifications du DOM.

```js

const observer = new MutationObserver((mutationsList) => {
  mutationsList.forEach((mutation) => {
    console.log('Mutation détectée:', mutation);
  });
});

observer.observe(document.getElementById('element'), { attributes: true, childList: true, subtree: true });
  
```

### Événements de données (WebSocket ou serveurs de données)

**message :** Se déclenche lorsque des données sont reçues via un WebSocket.

```js

const socket = new WebSocket('wss://example.com/socket');
socket.addEventListener('message', function(event) {
  console.log('Message reçu:', event.data);
});
  
```

### Autres événements de document

**fullscreenchange :** Se déclenche lorsque la page passe en mode plein écran ou en sort.

```js

document.addEventListener('fullscreenchange', function() {
  console.log('Mode plein écran changé');
});
  
```
