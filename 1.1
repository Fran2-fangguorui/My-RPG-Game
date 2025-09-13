#include <iostream>
#include <vector>
#include <string>
#include <cstdlib>
#include <ctime>
#include <algorithm>

using namespace std;

// 物品类
class Item {
private:
    string name;
    string description;
    int attackBonus;  // 攻击加成
    int defenseBonus; // 防御加成
    int healthRestore;// 恢复生命值
    bool isWeapon;    // 是否是武器
    bool isArmor;     // 是否是防具
    bool isConsumable;// 是否是消耗品

public:
    Item(string n, string d, int ab, int db, int hr, bool iw, bool ia, bool ic)
        : name(n), description(d), attackBonus(ab), defenseBonus(db), 
          healthRestore(hr), isWeapon(iw), isArmor(ia), isConsumable(ic) {}

    string getName() const { return name; }
    string getDescription() const { return description; }
    int getAttackBonus() const { return attackBonus; }
    int getDefenseBonus() const { return defenseBonus; }
    int getHealthRestore() const { return healthRestore; }
    bool isWeaponItem() const { return isWeapon; }
    bool isArmorItem() const { return isArmor; }
    bool isConsumableItem() const { return isConsumable; }
};

// 角色基类
class Character {
protected:
    string name;
    int level;
    int health;
    int maxHealth;
    int attack;
    int defense;
    int experience;

public:
    Character(string n, int l, int h, int a, int d)
        : name(n), level(l), health(h), maxHealth(h), attack(a), defense(d), experience(0) {}

    virtual ~Character() {}

    string getName() const { return name; }
    int getLevel() const { return level; }
    int getHealth() const { return health; }
    int getMaxHealth() const { return maxHealth; }
    int getAttack() const { return attack; }
    int getDefense() const { return defense; }
    int getExperience() const { return experience; }

    void setHealth(int h) { 
        health = h; 
        if (health > maxHealth) health = maxHealth;
        if (health < 0) health = 0;
    }

    void addExperience(int exp) { 
        experience += exp; 
        checkLevelUp();
    }

    virtual void checkLevelUp() {
        int requiredExp = level * 100;
        while (experience >= requiredExp) {
            experience -= requiredExp;
            level++;
            maxHealth += 20;
            attack += 5;
            defense += 3;
            health = maxHealth;
            cout << name << "升级到了" << level << "级！" << endl;
            requiredExp = level * 100;
        }
    }

    virtual int attackEnemy(Character& enemy) {
        int damage = max(1, attack - enemy.defense / 2);
        enemy.setHealth(enemy.getHealth() - damage);
        return damage;
    }

    bool isAlive() const { return health > 0; }
};

// 玩家类
class Player : public Character {
private:
    int hunger;       // 饥饿度 0-100
    int thirst;       // 口渴度 0-100
    vector<Item> inventory; // 物品栏
    Item* equippedWeapon;   // 装备的武器
    Item* equippedArmor;    // 装备的防具

public:
    Player(string n) : Character(n, 1, 100, 10, 5) {
        hunger = 0;
        thirst = 0;
        equippedWeapon = NULL;
        equippedArmor = NULL;
    }

    void addItem(Item item) {
        inventory.push_back(item);
        cout << "获得了" << item.getName() << "！" << endl;
    }

    void showInventory() const {
        if (inventory.empty()) {
            cout << "物品栏为空" << endl;
            return;
        }
        
        cout << "===== 物品栏 =====" << endl;
        for (unsigned int i = 0; i < inventory.size(); i++) {
            cout << i+1 << ". " << inventory[i].getName() << " - " << inventory[i].getDescription() << endl;
        }
        cout << "==================" << endl;
    }

    void useItem(int index) {
        if (index < 1 || index > (int)inventory.size()) {
            cout << "无效的物品编号" << endl;
            return;
        }
        
        Item& item = inventory[index-1];
        
        if (item.isConsumableItem()) {
            setHealth(getHealth() + item.getHealthRestore());
            cout << "使用了" << item.getName() << "，恢复了" << item.getHealthRestore() << "点生命值！" << endl;
            inventory.erase(inventory.begin() + index - 1);
        }
        else if (item.isWeaponItem()) {
            equippedWeapon = &item;
            cout << "装备了" << item.getName() << endl;
        }
        else if (item.isArmorItem()) {
            equippedArmor = &item;
            cout << "装备了" << item.getName() << endl;
        }
    }

    void updateSurvivalStats() {
        hunger = min(100, hunger + 1);
        thirst = min(100, thirst + 1);
        
        // 饥饿和口渴会造成伤害
        if (hunger >= 80) {
            setHealth(getHealth() - 1);
            if (hunger % 20 == 0) cout << "你非常饥饿！" << endl;
        }
        
        if (thirst >= 80) {
            setHealth(getHealth() - 1);
            if (thirst % 20 == 0) cout << "你非常口渴！" << endl;
        }
    }

    void eatFood() {
        // 查找食物
        for (vector<Item>::iterator it = inventory.begin(); it != inventory.end(); ++it) {
            if (it->getName() == "浆果" || it->getName() == "肉") {
                hunger = max(0, hunger - 30);
                cout << "你吃了" << it->getName() << "，感觉不那么饿了。" << endl;
                inventory.erase(it);
                return;
            }
        }
        cout << "你没有可以吃的食物！" << endl;
    }

    void drinkWater() {
        // 查找水
        for (vector<Item>::iterator it = inventory.begin(); it != inventory.end(); ++it) {
            if (it->getName() == "清水") {
                thirst = max(0, thirst - 40);
                cout << "你喝了水，感觉不那么渴了。" << endl;
                inventory.erase(it);
                return;
            }
        }
        cout << "你没有可以喝的水！" << endl;
    }

    int getHunger() const { return hunger; }
    int getThirst() const { return thirst; }

    // 重写攻击方法，考虑装备加成
    int attackEnemy(Character& enemy) {
        int totalAttack = attack;
        if (equippedWeapon) {
            totalAttack += equippedWeapon->getAttackBonus();
        }
        int damage = max(1, totalAttack - enemy.getDefense() / 2);
        enemy.setHealth(enemy.getHealth() - damage);
        return damage;
    }

    // 重写获取防御方法，考虑装备加成
    int getDefense() const {
        int totalDefense = defense;
        if (equippedArmor) {
            totalDefense += equippedArmor->getDefenseBonus();
        }
        return totalDefense;
    }

    void showStatus() const {
        cout << "===== " << name << " 的状态 =====" << endl;
        cout << "等级: " << level << "  经验: " << experience << "/" << level * 100 << endl;
        cout << "生命值: " << health << "/" << maxHealth << endl;
        cout << "攻击: " << attack;
        if (equippedWeapon) cout << " +" << equippedWeapon->getAttackBonus();
        cout << endl;
        cout << "防御: " << defense;
        if (equippedArmor) cout << " +" << equippedArmor->getDefenseBonus();
        cout << endl;
        cout << "饥饿度: " << hunger << "/100  口渴度: " << thirst << "/100" << endl;
        cout << "==========================" << endl;
    }
};

// 怪物类
class Monster : public Character {
private:
    int expReward;    // 击败后获得的经验
    string monsterType;

public:
    Monster(string type, int level) 
        : Character(type, level, 30 + level * 15, 5 + level * 5, 2 + level * 3) {
        monsterType = type;
        expReward = 20 + level * 10;
    }

    int getExpReward() const { return expReward; }
    string getMonsterType() const { return monsterType; }
};

// 地图位置类
class MapLocation {
private:
    string name;
    string description;
    bool hasMonster;
    bool hasItem;
    bool visited;

public:
    MapLocation(string n, string d, bool hm, bool hi)
        : name(n), description(d), hasMonster(hm), hasItem(hi), visited(false) {}

    string getName() const { return name; }
    string getDescription() const { return description; }
    bool getHasMonster() const { return hasMonster; }
    bool getHasItem() const { return hasItem; }
    bool isVisited() const { return visited; }

    void setVisited(bool v) { visited = v; }
    void setHasMonster(bool hm) { hasMonster = hm; }
    void setHasItem(bool hi) { hasItem = hi; }
};

// 游戏类
class Game {
private:
    Player player;
    vector<MapLocation> map;
    vector<Item> availableItems;
    int currentLocation;
    bool gameOver;

public:
    Game(string playerName) : player(playerName), currentLocation(0), gameOver(false) {
        // 初始化物品
        initItems();
        
        // 初始化地图
        initMap();
        
        // 设置随机数种子
        srand((unsigned int)time(NULL));
    }

    void initItems() {
        availableItems.push_back(Item("木剑", "一把简单的木剑", 5, 0, 0, true, false, false));
        availableItems.push_back(Item("石剑", "看起来有点钝了", 7, 0, 0, true, false, false));
        availableItems.push_back(Item("皮甲", "一件简陋的皮甲", 0, 3, 0, false, true, false));
        availableItems.push_back(Item("锁链甲", "一件由锁链编成的锁链甲", 0, 5, 0, false, true, false));
        availableItems.push_back(Item("铁剑", "一把坚固的铁剑", 10, 0, 0, true, false, false));
        availableItems.push_back(Item("铁甲", "一件耐用的铁甲", 0, 7, 0, false, true, false));
        availableItems.push_back(Item("治疗药水", "恢复生命值的药水", 0, 0, 30, false, false, true));
        availableItems.push_back(Item("浆果", "可以食用的野生浆果", 0, 0, 10, false, false, true));
        availableItems.push_back(Item("肉", "烤熟的肉", 0, 0, 25, false, false, true));
        availableItems.push_back(Item("清水", "干净的饮用水", 0, 0, 0, false, false, true));
        availableItems.push_back(Item("钻石剑", "一把锋利的钻石剑", 12, 0, 0, true, false, false));
        availableItems.push_back(Item("钻石甲", "一件超级坚硬的钻石甲", 0, 9, 0, false, true, false)); 
    }

    void initMap() {
        map.push_back(MapLocation("森林边缘", "你站在森林的边缘，周围有许多树木和灌木。", true, true));
        map.push_back(MapLocation("小溪边", "一条清澈的小溪流过这里，水看起来可以饮用。", true, true));
        map.push_back(MapLocation("洞穴入口", "一个黑暗的洞穴入口，里面似乎有什么东西在移动。", true, true));
        map.push_back(MapLocation("开阔草地", "一片开阔的草地，视野良好但缺乏掩护。", true, true));
        map.push_back(MapLocation("废弃营地", "一个被遗弃的营地，可能还留有一些有用的东西。", false, true));
        map.push_back(MapLocation("山顶", "山顶上，你可以看到很远的地方。", false, false));
    }

    void start() {
        cout << "欢迎来到生存RPG游戏！" << endl;
        cout << "你的名字是：" << player.getName() << endl;
        cout << "你的目标是在这个危险的世界中生存下去，变得更强！" << endl;
        cout << "输入h可以查看命令列表。" << endl << endl;
        
        // 给玩家初始物品
        player.addItem(availableItems[5]); // 浆果
        player.addItem(availableItems[7]); // 清水
        
        gameLoop();
    }

    void gameLoop() {
        while (!gameOver) {
            // 显示当前位置信息
            showCurrentLocation();
            
            // 更新生存状态
            player.updateSurvivalStats();
            
            // 检查玩家是否还活着
            if (!player.isAlive()) {
                gameOver = true;
                cout << "你已经死亡，游戏结束。" << endl;
                break;
            }
            
            // 获取玩家输入
            string command;
            cout << "请输入命令: ";
            cin >> command;
            
            // 处理命令
            processCommand(command);
        }
    }

    void showCurrentLocation() {
        cout << endl << "===== " << map[currentLocation].getName() << " =====" << endl;
        cout << map[currentLocation].getDescription() << endl;
        
        if (!map[currentLocation].isVisited()) {
            // 第一次来到这个地方，可能会触发事件
            checkLocationEvents();
            map[currentLocation].setVisited(true);
        }
    }

    void checkLocationEvents() {
        // 检查是否有怪物
        if (map[currentLocation].getHasMonster() && rand() % 3 != 0) {
            int monsterLevel = player.getLevel() + (rand() % 3 - 1);
            if (monsterLevel < 1) monsterLevel = 1;
            
            string monsterType;
            switch (rand() % 3) {
                case 0: monsterType = "野狼"; break;
                case 1: monsterType = "巨蜘蛛"; break;
                case 2: monsterType = "僵尸"; break;
                default: monsterType = "怪物";
            }
            
            Monster monster(monsterType, monsterLevel);
            cout << "一只" << monster.getMonsterType() << "出现了！等级: " << monster.getLevel() << endl;
            battle(monster);
        }
        
        // 检查是否有物品
        if (map[currentLocation].getHasItem() && rand() % 4 != 0) {
            int itemIndex = rand() % availableItems.size();
            Item foundItem = availableItems[itemIndex];
            player.addItem(foundItem);
            map[currentLocation].setHasItem(false); // 拿走物品后就没有了
        }
    }

    void battle(Monster& monster) {
        cout << "战斗开始！" << endl;
        
        while (player.isAlive() && monster.isAlive()) {
            // 玩家回合
            cout << endl << "你的回合:" << endl;
            cout << "1. 攻击  2. 查看状态" << endl;
            int choice;
            cin >> choice;
            
            if (choice == 1) {
                int damage = player.attackEnemy(monster);
                cout << "你对" << monster.getName() << "造成了" << damage << "点伤害！" << endl;
                
                if (!monster.isAlive()) {
                    cout << "你击败了" << monster.getName() << "！" << endl;
                    player.addExperience(monster.getExpReward());
                    break;
                }
            }
            else if (choice == 2) {
                player.showStatus();
                cout << monster.getName() << " - 生命值: " << monster.getHealth() << "/" << monster.getMaxHealth() << endl;
                continue;
            }
            
            // 怪物回合
            int monsterDamage = monster.attackEnemy(player);
            cout << monster.getName() << "对你造成了" << monsterDamage << "点伤害！" << endl;
            cout << "你的生命值: " << player.getHealth() << "/" << player.getMaxHealth() << endl;
        }
    }

    void processCommand(string command) {
        if (command == "n" || command == "s" || command == "east" || command == "w") {
            movePlayer();
        }
        else if (command == "st") {
            player.showStatus();
        }
        else if (command == "i") {
            player.showInventory();
            cout << "输入u 编号 使用物品，或输入back返回" << endl;
            string subCommand;
            cin >> subCommand;
            if (subCommand == "u") {
                int index;
                cin >> index;
                player.useItem(index);
            }
        }
        else if (command == "e") {
            player.eatFood();
        }
        else if (command == "d") {
            player.drinkWater();
        }
        else if (command == "h") {
            showHelp();
        }
        else if (command == "q") {
            gameOver = true;
            cout << "游戏结束，再见！" << endl;
        }
        else {
            cout << "未知命令，请输入help查看可用命令。" << endl;
        }
    }

    void movePlayer() {
        int newLocation = rand() % map.size();
        while (newLocation == currentLocation) {
            newLocation = rand() % map.size();
        }
        currentLocation = newLocation;
        cout << "你移动到了新的地方。" << endl;
    }

    void showHelp() {
        cout << "===== 命令列表 =====" << endl;
        cout << "n/s/east/w - 向不同方向移动" << endl;
        cout << "st - 查看你的状态" << endl;
        cout << "i - 查看物品栏" << endl;
        cout << "e - 吃东西" << endl;
        cout << "d - 喝水" << endl;
        cout << "h - 显示帮助信息" << endl;
        cout << "q - 退出游戏" << endl;
        cout << "====================" << endl;
    }
};

int main() {
    string playerName;
    cout << "请输入你的名字: ";
    cin >> playerName;
    
    Game game(playerName);
    game.start();
    
    return 0;
}
