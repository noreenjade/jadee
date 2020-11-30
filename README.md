firstturn =1
class Warrior:
 def __init__(self):
     self.Name = "Name"
     self.HP = 100
     self.Attack = 1
     self.Defense = 1
     self.Speed = 50
 def equipWeapon(self):
    chosenweapon= int(input("Choose your weapon:\n\n\t 1.) Dagger : +20 Atk -0 Spd \n\n\t 2.)Sword : +30 Atk -10 Spd \n\n\t 3.) Axe : +40 Atk -20 Spd\n "))
    if chosenweapon <= 3:
        Weapon.getAttrib(self,chosenweapon)
 
 def equipArmor(self):
    chosenarmor= int(input("Choose your armor:\n\n\t 1.) Light : +15 Def -5 Spd \n\n\t 2.) Medium : +25 Def -15 Spd \n\n\t 3.) Heavy : +35 Def -25 Spd\n "))
 
    if chosenarmor <= 3:
        Armor.getAttrib(self,chosenarmor)
 
 def rename(self):
     self.Name = str(input("What would you name your character? : "))
 
 def getDamaged(self,Damage):
     self.HP -= Damage
 
class Weapon:
 def __init__(self,WSpeedPen,Attack):
     self.WSpeedPen = WSpeedPen
     self.Attack = Attack
 
 def getAttrib(self,chosenweapon):
    if chosenweapon == 1:
        self.Attack += 20
        self.Speed -= 0
    elif chosenweapon == 2:
        self.Attack += 30
        self.Speed -= 10
    elif chosenweapon == 3:
        self.Attack += 40
        self.Speed -= 20
 
 
class Armor:
 def __init__(self,WSpeedPen,Defense):
     self.WSpeedPen = WSpeedPen
     self.Defense = Defense
 
 def getAttrib(self,chosenarmor):
     if chosenarmor == 1:
        self.Defense += 15
        self.Speed -= 5
     elif chosenarmor == 2:
        self.Defense += 25
        self.Speed -= 15
     elif chosenarmor == 3:
        self.Defense += 35
        self.Speed -= 25
 
class Environment:
 def __init__(self):
         self.Plpenalty = 0
         self.OpPenalty = 0
         self.Name = "Name"
 
 def chooseEnv(self) :
     chosenmap= int(input("Choose your Map:\n\n\t 1.) Arena : No effects \n\n\t 2.) Swamp :Player -1HP per turn | -+1 atk to enemy \n\n\t 3.) Colloseum :Player +1 Atk || Enemy -1 Def\n"))
 
     if chosenmap == 1:
         self.Plpenalty += 0
         self.OpPenalty += 0
         self.Name = "Arena"
     elif chosenmap == 2:
         self.Plpenalty = 1
         self.OpPenalty = 1
         self.Name = "Swamp"
     elif chosenmap == 3:
         self.Plpenalty = 1
         self.OpPenalty = 1
         self.Name = "Colloseum"
 
 def getname(self) :
     return self.Name
 
 def envFX(self,chosenmap,firstturn):
     if chosenmap == 2:
        Warrior.getDamaged(self,self.Plpenalty)
        if firstturn == 1 :
           Opponent.Attack += self.OpPenalty
           firstturn = 0
 
     elif chosenmap == 3:
        if firstturn == 1 :
            Opponent.Defense -= self.OpPenalty
            Warrior.Attack += self.Plpenalty
            firstturn = 0
 
 
class Opponent:
 def __init__(self):
     self.HP = 0
     self.Attack = 0
     self.Defense = 0
     self.Speed = 0
     self.Name = "Enemy"
 
 def chooseEnemy(self) :
    chosenenemy= int(input("Choose your Enemy:\n\n\t 1.) Thief HP: 150 || ATK: 20 || Def: 10 || Spd: 40 \n\n\t 2.) Viking HP: 250 || ATK: 30 || Def: 20 || Spd: 30 \n\n\t 3.) Minotaur HP: 350 ||ATK: 40 || Def: 30 || Spd: 20\n "))
