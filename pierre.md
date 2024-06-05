# Pierre feuille ciseaux

## Step 1 
 
Bienvenue! Créer deux variables, ``||variables:joueur1||`` et  ``||variables:joueur2||``.
Placer le bloc ``||variables:définir joueur1 à 0||`` et le bloc ``||variables:définir joueur2 à 4||`` dans l'événement ``||basic:au démarrage||``.

```blocks
let joueur1 = 0
let joueur2 = 4
```

## Step 2 
 
Définir le groupe ``||radio||`` et placer le bloc dans l'événement ``||basic:au démarrage||``.
 
```blocks
let joueur1 = 0
let joueur2 = 4
radio.setGroup(1)
```

## Step 3
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

## Step 4
Sélectionne l'événement ``||input:lorsque le bouton «B» est pressé||`` ajoute le bloc : ``||variables: définir joueur2 à 2 ||`` , ajoute le bloc ``|| basic: montrer feuille||`` , ajoute le bloc ``||basic: pause||``
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

## Step 5
Sélectionne l'événement ``||input:lorsque les boutons «A» et «B» sont pressés||`` ajoute le bloc : ``||variables: définir joueur2 à 3 ||`` , ajoute le bloc ``|| basic: montrer feuille||`` , ajoute le bloc ``||basic: pause||``
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
## Step 6
 Si vous voulez pour gagner du temps et vous éviter de rentrer le code ci-dessous vous pouvez faire un copier coller de cette partie à partir du programme précédent.
 Pour cela il vous faut l'ouvrir dans une autre fenêtre.
 
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

