# Pierre feuille ciseaux

## Etape 1 
 
Bienvenue! Créer deux variables, ``||variables:joueur1||`` et  ``||variables:joueur2||``.
Dans l'événement ``||basic:au Démarrage||`` Placer le bloc ``||variables:définir joueur1 à 0||`` et le bloc ``||variables:définir joueur2 à 4||``.

```blocks
let joueur1 = 0
let joueur2 = 4
```

## Etape 2 
 
Définir le groupe ``||radio||`` et placer le bloc dans l'événement ``||basic:au Démarrage||``.
 
```blocks
let joueur1 = 0
let joueur2 = 4
radio.setGroup(1)
```

## Etape 3
Sélectionne l'événement ``||input:lorsque le bouton «A» est pressé||`` ajoute le bloc : ``||variables: définir joueur2 à 1 ||`` , ajoute le bloc ``|| basic: montrer feuille||`` , ajoute le bloc ``||basic: pause||``
ajoute également ``||radio: envoyer nombre par radio||``.

```blocks
input.onButtonPressed(Button.A, function () {
    joueur2 = 1
    basic.showLeds(`
        # # # # #
        # . . . #
        # . . . #
        # . . . #
        # # # # #
        `)
    basic.pause(1000)
    radio.sendNumber(joueur2)
})
```

## Etape 4
Sélectionne l'événement ``||input:lorsque le bouton «B» est pressé||`` ajoute le bloc : ``||variables: définir joueur2 à 2 ||`` , ajoute le bloc ``|| basic: montrer pierre||`` , ajoute le bloc ``||basic: pause||``
ajoute également ``||radio: envoyer nombre par radio||``.
```blocks
input.onButtonPressed(Button.B, function () {
    joueur2 = 2
    basic.showLeds(`
        . . . . .
        . # # # .
        . # # # .
        . # # # .
        . . . . .
        `)
    basic.pause(1000)
    radio.sendNumber(joueur2)
})
```

## Etape 5
Sélectionne l'événement ``||input:lorsque les boutons «A» et «B» sont pressés||`` ajoute le bloc : ``||variables: définir joueur2 à 3 ||`` , ajoute le bloc ``|| basic: montrer ciseaux||`` , ajoute le bloc ``||basic: pause||``
ajoute également ``||radio: envoyer nombre par radio||``.
```blocks
input.onButtonPressed(Button.AB, function () {
    joueur2 = 3
    basic.showLeds(`
        # # . . #
        # # . # .
        . . # . .
        # # . # .
        # . . . #
        `)
    basic.pause(1000)
    radio.sendNumber(joueur2)
    ```
## Etape 6
 Sélectionne l'événement ``||input:lorsqu'une donnée reçu par radio||`` , ajoute ``||variables:définir joueur1 reçu numéro||``

```blocks
radio.onReceivedNumber(function (receivedNumber) {
    joueur1 = receivedNumber
```

## Etape 7
Placer un bloc ``||logic:si alors||`` et tester l'égalité ``||logic:=||`` entre ``||variables:joueur1||`` et ``||variables:joueur2||``, placer un bloc ``||basic: icône sleep||``
```blocks
radio.onReceivedNumber(function (receivedNumber) {
    joueur1 = receivedNumber
    if (joueur1 == joueur2) {
        basic.showIcon(IconNames.Asleep)
    }
```
## Etape 8

Placer un bloc ``||logic:si alors||`` et tester si le joueur1 = 1. 
Placer un bloc ``||logic:si sinon||``  et tester si le joueur2 = 2. 
Placer un bloc ``||basic: icône triste||``.
Placer dans la partie ``||logic:sinon||`` un bloc ``||logic:si alors||`` et tester si le joueur2 = 3.
Placer un bloc ``||basic: icône heureux||`` 


```blocks
radio.onReceivedNumber(function (receivedNumber) {
    joueur1 = receivedNumber
    if (joueur1 == joueur2) {
        basic.showIcon(IconNames.Asleep)
    }
    if (joueur1 == 1) {
        if (joueur2 == 2) {
            basic.showIcon(IconNames.Sad)
        } else {
            if (joueur2 == 3) {
                basic.showIcon(IconNames.Happy)
            }
        }
    }
```
## Etape 9

Continuer de la même façon pour terminer le programme 
```blocks
    radio.onReceivedNumber(function (receivedNumber) {
    joueur1 = receivedNumber
    if (joueur1 == joueur2) {
        basic.showIcon(IconNames.Asleep)
    }
    if (joueur1 == 1) {
        if (joueur2 == 2) {
            basic.showIcon(IconNames.Sad)
        } else {
            if (joueur2 == 3) {
                basic.showIcon(IconNames.Happy)
            }
        }
    }
    if (joueur1 == 2) {
        if (joueur2 == 1) {
            basic.showIcon(IconNames.Happy)
        } else {
            if (joueur2 == 3) {
                basic.showIcon(IconNames.Sad)
            }
        }
    }
    if (joueur1 == 3) {
        if (joueur2 == 1) {
            basic.showIcon(IconNames.Sad)
        } else {
            if (joueur2 == 2) {
                basic.showIcon(IconNames.Happy)
            }
        }
    }
    basic.pause(1000)
    })
```
## Félicitations !
#### vous avez terminer, vous pouvez maintenant jouer.
