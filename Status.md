# BULK Confirmation: 
- [x] Require All the selected Grants

# CA000 - Global

seperated Authentication transfer and device code flow 
Changed all to Auth Strength MFA 
Renamed all groups to match. 
Added RegisterSecurity Information CA policy

CA060 - Der skal laves ekstra ting i sharepoint for at den virker 
CA001 - Guest skal være ekskluderet.

# CA 100 - Admins

Changed to Auth Strength 
Added Version Number
Verified Groups 
Added RegisterSecurity Information CA policy


# CA300 - Guests

# Naming Standard
CA000-CSB-LVL1-Global-IdentityProtection-AnyApp-AnyPlatform-StrengthMFA-v1.0

CA{N=Persona}{PolicyNumb}

## Policynumb
00-19 - IdentityProtection
20-29 - SessionProtection
30-49 - AttackSurfaceReduction
50-59 - DeviceProtection
60-69 - DataProtection
70-99 - Reserved

# Persona Descriptions: 
- 000 Global
 - These policies in general will apply to all persona groups, see them as catch all polcies, there will be exclusions but those will be very thought out, as these are bare minimum restrictions everyone at least has to follow, then other personas might put on higher restrictions
- 100 Admins 
- 200 Users
- 300 Guests 
- 400 Break glass
- 500 Service Accounts
- 600 Agents


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

