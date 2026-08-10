# BULK Confirmation: 
- [x] Require All the selected Grants

# CA000 - Global

seperated Authentication transfer and device code flow 
Changed all to Auth Strength MFA 
Renamed all groups to match. 
Added RegisterSecurity Information CA policy

CA006 - Der skal laves ekstra ting i sharepoint for at den virker 
CA008 - Guest skal være ekskluderet.

# CA 100 - Admins

Changed to Auth Strength 
Added Version Number
Verified Groups 
Added RegisterSecurity Information CA policy


# CA200 - Guests

# Naming Standard
CA000-CSB-LVL1-Global-IdentityProtection-AnyApp-AnyPlatform-StrengthMFA-v1.0

CA{N=Persona}{PolicyNumb}

## Policynumb
00-20 - IdentityProtection
21-40 - AttackSurfaceReduction
41-60 - DeviceProtection
61-70 - SessionProtection
71-80 - Not yet defined
81-90 - Not yet defined
91-99 - Not yet defined

# Talk to Philip
- Baseline er en baseline T1,T2,T3. Men stadig en baseline baseline noget alle ville ku deploye. Måske man kunne lave et repo mere som er sårn mere et CA katalog man kan plukke fra hvor det lidt mere hey! læs lige op på de her inden du bare smadre dem på. 

- Internals, Vi burde også have interals. 

# TODO
Device Code flow måske nogle admins har brug for det? hvordan tager vi højde for det?

# Persona Descriptions: 
- 000 Global
 - These policies in general will apply to all persona groups, see them as catch all polcies, there will be exclusions but those will be very thought out, as these are bare minimum restrictions everyone at least has to follow, then other personas might put on higher restrictions
- 100 Admins 
- 200 Guests 
- 300 Service Accounts
- 400 Agents
- 500 Inter


# Baseline Levels
This baseline is seperated into differnet levels to show you easily where to start when implamenting this baseline, these levels are not facts but our personal opionins on whats most important. 

- Level 1
    - All tenants should have these polciies in place, whether you are 5 or 5000 employees in the org. 
- Level 2
    - You want to strengthen your security and minimize the affect on standard employees. 
- Level 3
    - You have secured the most critical assets: admins, Serice Accounts etc. and are ready to implement heavier security requirements for users and devices. 
- Level 4
    - You are ready to compromise on Workability, you wory more about security than on a user not being able to work for a day or two.
- Level 5 
    - You are a Large enterprise or a special company requireing maximum foundational security.