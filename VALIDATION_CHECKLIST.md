# Validation Checklist for BloodyAllegiance Optimizations

## Pre-Testing Setup
- [ ] Back up current working mod files
- [ ] Ensure BG3 Mod Manager is installed
- [ ] Have a test save ready in BG3

## File Integrity Checks
- [x] All 13 weapon entries present (11 weapons + 2 base templates)
- [x] No duplicate spell definitions
- [x] Syntax appears valid (proper quotes, semicolons)
- [x] File reduced from 736 to 617 lines (16.2% reduction)

## BG3 Mod Manager Validation
- [ ] Load mod in BG3 Mod Manager
- [ ] Check for parsing errors
- [ ] Verify no warnings or conflicts reported
- [ ] Confirm mod shows as "Valid" status

## In-Game Testing - Base Template Properties
Test that all weapons inherit common properties from base templates:

### Common Properties (All Weapons)
- [ ] Force damage type
- [ ] VeryRare rarity (except Mage variants)
- [ ] Item returns to owner
- [ ] Magical property
- [ ] Enchantment scales with level (2/3/5)
- [ ] All 6 spells unlock on equip
- [ ] All 3 description passives (Desc_1, Desc_2, Desc_3)
- [ ] All 7 main hand passives apply
- [ ] Status on equip works
- [ ] Critical hits heal for DamageDone/8

### One-Handed Weapons
Test 2-3 variants to confirm base inheritance:

#### BloodyAllegiance_Aluve
- [ ] Spawns with correct model
- [ ] Shows Force damage
- [ ] Has NotSheathable property
- [ ] All common properties work

#### BloodyAllegiance_Silver_OneHand
- [ ] Spawns with correct model
- [ ] Can be sheathed (no NotSheathable)
- [ ] All common properties work

#### BloodyAllegiance_Giant_Onehand_Mage
- [ ] Shows Legendary rarity (not VeryRare)
- [ ] Uses Toggled_MainMagic_Apply_Sumoned passive
- [ ] All other common properties work

### Two-Handed Weapons
Test both variants:

#### BloodyAllegiance_Giant_Twohand
- [ ] Spawns with correct model
- [ ] Shows 2d8 damage
- [ ] Twohanded property
- [ ] All common properties work

#### BloodyAllegiance_Crusher_TwoHand
- [ ] Spawns with correct model
- [ ] SimpleMeleeWeapon group
- [ ] All common properties work

### Rapier
#### BloodyAllegiance_Rapier
- [ ] Spawns with rapier model
- [ ] Shows 1d8 damage
- [ ] Value is 25000 (not 2500)
- [ ] All common properties work

## Spell and Ability Testing
For 2-3 weapons, verify:
- [ ] All 6 demonic spells unlock on equip:
  - [ ] Target_Duo_Demonic
  - [ ] Zone_Cleave_Demonic
  - [ ] Target_Heart_Demonic
  - [ ] Zone_Fear_Demonic2
  - [ ] TerrorOnslaught_Original_Demon
  - [ ] Awok_Terror_Demonic

- [ ] Passives activate correctly:
  - [ ] Critical hits trigger effects
  - [ ] Kill blows trigger effects
  - [ ] Souls Torment system works

## Combat Testing
- [ ] Attack with weapon - damage applies correctly
- [ ] Critical hit - healing triggers
- [ ] Kill enemy - kill passive triggers
- [ ] Multiple kills - Souls Torment counter increases
- [ ] End combat - Souls Torment tier applies

## Performance Testing
- [ ] Note mod load time in BG3 Mod Manager
- [ ] Check game startup time
- [ ] Monitor memory usage (if possible)
- [ ] Compare to pre-optimization performance

## Edge Cases
- [ ] Equip/unequip multiple times
- [ ] Switch between different variants
- [ ] Dual-wield compatible weapons
- [ ] Drop and pick up weapon
- [ ] Send to camp and retrieve

## Rollback Plan
If issues are found:
1. Git revert to commit before optimizations
2. Document which specific weapon/property failed
3. Investigate inheritance chain issue
4. Apply targeted fix

## Known Limitations
- Base templates are new entries; they will appear in mod manager but should not be spawnable in-game
- If base template is somehow spawned, it would have generic longsword appearance

## Success Criteria
- [ ] All weapons spawn correctly
- [ ] All inherited properties work
- [ ] All overridden properties work
- [ ] No parsing errors
- [ ] No game crashes
- [ ] Performance is same or better than before

## Documentation Verification
- [x] OPTIMIZATION_SUMMARY.md created
- [x] IMPROVEMENTS_GUIDE.md created
- [x] This validation checklist created

## Sign-Off
- Tester Name: _______________
- Date: _______________
- Result: [ ] PASS [ ] FAIL [ ] NEEDS WORK
- Notes: _______________________________________________
