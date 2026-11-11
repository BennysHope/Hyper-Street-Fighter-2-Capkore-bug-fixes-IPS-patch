Vibe coded by BennysHope
CapKore (PS2 SLPM-66636) gameplay fixes ported to CPS2 Hyper Street Fighter II 040202
(hsf2j and hsf2 USA). The patches go on the ENCRYPTED program ROMs: opcodes are re-encrypted per address, and data is written as plain bytes.
They work with the original .key, so the set stays the stock encrypted parent/clone. Only the CRCs change, so MAME reports WRONG CHECKSUMS but runs it.

68k addr   change                                   fix
0x071E30   38-byte block rewrite (decrypted)        Blanka WW Rock Crusher range: new <0x60 distance check (CK logic)
0x09A332   C200 -> C240  and.b d0,d1 -> and.w       Guile WW Somersault strength (was always light)
0x09A1C4   C200 -> C240  (Sonic, cosmetic mirror of CK, no behaviour change)
0x07F9B6   6618 -> 6606  bne -> strength calc       Claw wall jump/climb: kick-press path skipped strength calc (index=#$700 garbage)
0x091D50   6618 -> 6606  same, second Claw copy
0x0874AC   2E 30 32 -> 26 28 2A  (data)             Sagat Low Tiger recovery = High Tiger (table 1)
0x087634   2E 2E 2E -> 26 26 26  (data)             Sagat Low Tiger recovery = High Tiger (table 2)

ips/hsf2j : against hs2j.03c CRC 6efe661f / hs2j.04b CRC 93f2500a
ips/hsf2  : against hs2u.03 CRC b308151e / hs2u.04 CRC 327aa49c
The hsf2j IPS also applies cleanly on top of the English restoration's 03c/04b. There is no byte overlap, and CPS2 encryption is per address, so the result is valid.
mame/capkore/hsf2j.zip, mame/capkore/hsf2.zip, mame/english+capkore/hsf2j.zip
