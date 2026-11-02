# Radio recommendations

Receivers worth considering as an upgrade over, or companion to, the Eton Elite Executive and the Kenwood TH-D75, plus antennas and bags for the TH-D75. Written 2026-11-02 from general knowledge, not current listings: prices are rough, and models come and go, so check availability and reviews before buying.

## What the current radios cover

| | Eton Elite Executive | Kenwood TH-D75 |
|---|---|---|
| Shortwave / HF | Yes, with SSB | Receive only, no SSB, weak stock antenna |
| Airband (118–136 MHz) | Yes, but strong local FM can overload it | Yes (band B) |
| NOAA weather, 2 m / 70 cm, MURS, GMRS | No | Yes |
| Military UHF aviation (225–400 MHz) | No | Yes (band B) |
| Computer programming | No | Yes |
| Digital public safety (P25 trunked) | No | No |

## Same kind of radio, but better (shortwave, SSB, airband)

| Radio | Rough price | Why |
|---|---|---|
| Sangean ATS-909X2 | $250–300 | Often called the best traditional portable: excellent shortwave sensitivity, good SSB and airband, and better at handling strong-signal overload than the Eton |
| Tecsun PL-680 | ~$130 | Shortwave, SSB, airband and synchronous AM detection, which reduces fading on shortwave. Good value |
| XHDATA D-808 | ~$80 | Budget pick with shortwave, SSB and airband; close to the Eton for much less |

## Covers far more (wideband handheld receivers)

| Radio | Rough price | Why |
|---|---|---|
| Malahit DSP2 (standalone SDR) | $300–450 | Tunes 10 kHz–2 GHz with SSB, airband, NOAA, military UHF and 2 m / 70 cm, plus a live waterfall display. Covers the Eton's and the D75's receive range in one box. Buy from a reputable seller; clones are common |
| Icom IC-R30 | $650–700 | Polished wideband handheld, 100 kHz–3.3 GHz, SSB, two receivers at once, some digital voice modes, and computer programming |

## Digital public safety (P25 trunked)

Tucson and Pima County police, fire and EMS use PCWIN (Pima County Wireless Integrated Network), which RadioReference lists as a **P25 Phase II** system on 800 MHz. It's also a **simulcast** system, where several towers transmit the same signal at once, and cheaper digital scanners often decode that poorly. Neither the TH-D75 nor the Eton can receive it.

| Option | Rough price | Why |
|---|---|---|
| Uniden SDS200 (base / mobile) | ~$700 | Best fit for PCWIN: decodes Phase II and handles simulcast better than older scanners; the stronger of the two SDS models |
| Uniden SDS100 (handheld) | ~$500–600 | The handheld version of the SDS200, with the same Phase II decoding and better simulcast handling than older scanners |
| Whistler TRX-1 / TRX-2 | ~$400–550 | Decodes Phase II; simulcast performance less certain |
| RTL-SDR USB receiver + SDRTrunk (free software) on the Mac | ~$40 | Decodes Phase II and copes with simulcast reasonably well. Tied to a computer, but a cheap way to see what's in the clear before buying a scanner |
| Broadcastify (website / app) | Free | Online streams of many Tucson and Pima County feeds; no radio needed |

Notes:
- **Skip the older Uniden BCD436HP / BCD536HP for PCWIN.** They decode Phase II, but users report trouble with simulcast systems like it.
- **Encryption:** no scanner can decode encrypted talkgroups. Marana Police is confirmed as always encrypted. Whether Tucson Police dispatch is encrypted is unclear: forum posts from different years disagree, and some say almost everything except Marana PD is in the clear. Fire and EMS are less often encrypted. Check RadioReference's PCWIN talkgroup list (it marks encrypted talkgroups) before buying.
- **Programming:** Uniden's Sentinel software is believed to be Windows-only, so on a Mac use a Windows virtual machine or program from the scanner itself.
- **Sources:** [RadioReference wiki – PCWIN](https://wiki.radioreference.com/index.php/Pima_County_Wireless_Integrated_Network_(PCWIN)), [RadioReference database – PCWIN](https://www.radioreference.com/db/sid/7735), [RadioReference forum – PCWIN Tucson](https://forums.radioreference.com/threads/pcwin-tucson.321191/).

## Recommendation

- **One radio that beats the Eton and fills the D75's gaps:** Malahit DSP2.
- **Mainly a better shortwave and SSB experience:** Sangean ATS-909X2.
- **Tucson police, fire and EMS:** try an RTL-SDR with SDRTrunk first, then buy a Uniden SDS200 (or SDS100 for a handheld) if enough is in the clear.

## TH-D75 antennas

The D75 is believed to have an SMA-female jack, like other Kenwood handhelds, so it needs an **SMA-male** antenna. Many cheap antennas are made for Baofeng radios, which use the opposite connector. Check the stock antenna's base before ordering: a center pin means male.

These are tuned for 2 m / 70 cm. They also improve reception on airband, NOAA, MURS and SO-50, but won't help much on WWV or CB.

| Antenna | Type | Why |
|---|---|---|
| Komunica foldable (sold by WiMo) | Folding, 42 cm or 94 cm | Best-made foldable found. Get the 94 cm version for range, and order the SMA-male connector |
| Generic folding tactical (HYS, Abbree and similar) | Folding, 15–42 in | $15–25, dual-band 2 m / 70 cm, about 20 W. Good for the price, but quality varies, so get one whose listing clearly says SMA-male |
| Signal Stuff Signal Stick | Flexible whip | Not folding, but thin and flexible enough to bend flat in a pocket; sturdier than a folding antenna |
| Diamond SRH77CA | Short whip | Solid dual-band whip that beats the stock antenna on 2 m. Buy from a ham dealer, because counterfeits are common online |

## Bags and cases

Pick by how the radio will be carried. The brands below are well regarded; specific models weren't checked against current listings.

| Option | Examples | Best for |
|---|---|---|
| Radio chest rig or harness | Condor, Rothco radio chest rigs | Walking or hiking: the radio rides on your chest with the antenna up, and side pouches hold a spare battery and a short antenna |
| Small EDC sling or organizer bag | Maxpedition Fatty or Beefy organizers, small Maxpedition slings | An organized go-bag: padded, with elastic loops for batteries, cables and small antennas |
| Camera bag with movable dividers | Lowepro, Peak Design | A go-bag you can lay out around the radio, batteries and charger |
| Hard case with pick-apart foam | Pelican 1150 or 1200 | Car or storage: waterproof and crushproof |

Things to plan for:
- **Antenna length:** a 94 cm foldable folds to about half that length. Check the bag's inside length, or carry a shorter whip in the bag and the long antenna separately.
- **Battery storage:** keep spare lithium-ion batteries in a separate pocket, or put covers over their contacts, so they can't short against keys or metal.
- **Programming and charging:** pack a USB-C cable for programming and a charger, so the radio can be updated in the field.
