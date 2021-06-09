
# Pojezdy letadel

### Základní hiearchie
 
* Logic
* Map data
  * Item 2a
  * Item 2b

### Nastavení předního kolečka

Objekt musí mít jako defaultní rotaci 90° na ose X

1. Lokálně otočit o 90° dozadu
2. Podle 3D kurzoru v edit modu otočit o 90° zpět

### Pořadí materiálů

Materiál letadla musí být na prvním místě (před materiálem pilotů a skla)

1. Přesunout materiál letadla na první místo
2. V edit modu Mesh > Sort Elements... > Material
    - Elements: Faces

### Outline

- V objekt modu RMB > Shade smooth
- V edit modu Ctrl+E > Clear sharp
- Zvolit všechny Select > Select All by Trait > Non Manifold hrany a opravit aby model byl co nejvíc manifoldní na viditelných místech

### Nastavení motion parts

- Do text editoru importovat [setup skript](https://github.com/Haug-Land/BlenderUtilities/blob/main/airplane_parts_setup.py)
- V edit modu vybrat dvě hrany jejichž středy definují lokální osu otačení pohyblivé části
- Respektovat orientaci částí dle obrázku:

![](data/motion_parts_orientation.png)

### Světla

- Světla musí mít objektovou velikost 0.01
- Addon UV: Magic UV
- U > UVW > Box
- Parameter scale nastavit na 100

### Renderování

- Kameru Ctrl+C, ctrl+V z jiného éra, od oka napozicovat aby byli hezký marginy
- Nastavit rozlišení 2048x2048
- Nastavit Render properties
    - Film > Transparent
    - Color management > View transform > Standard
- Vypnout renderování kolekcí, které nepotřebujeme pro renderování ikonky letadla. Nechat pouze:
    - LOD0 bez Outline
    - Motion_Parts

### Paint model

- LOD0, Front wheel a motion parts spojit do jednoho objektu, dát do nové kolekce
- Smazat podle materiálu piloty a sklo

### Export

- File > Export > FBX (.fbx)
- Zaškrtnout Include > Limit to Selected Objects
- Odškrtnout sekci Bake Animation

# Unity

### U modelu remapovat materiály

- V inspectoru modelu On Demand Remap
- Naming: From model's Material
- Search: Project-Wide

### aabb

- Dotvořit chybějící materiály (minimálně base materiál letadla a stínu)
- Zkopírovat prefab letadla se stejným Tierem
- Vložit do prefabu nový model
- Popřiřazovat objekty
- Zvolit zvukový profil
- U motion parts přiřazuje se pivot
- Vytvořit data objekt letadla
- Přidat prefab do seznamu prefabů
- Přidat data objekt do seznamu data objektů