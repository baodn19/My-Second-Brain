---
excalidraw-plugin: parsed
tags:
  - excalidraw
  - "#Project"
categories:
  - "[[Projects]]"
year:
status:
  - ongoing
---
==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Related Experience

# Excalidraw Data

## Text Elements
Contribution ^KXSUf78F

- Real-time edge-cloud disease detection system
- Real field conditions ^Pkqreb3B

Disease: ^hqCfmCPI

Botrytis and anthracnose/ Classify 3 different fungal diseases that cause crown rot ^yxa7Iumd

Research Questions ^QAJlpX3j

Meeting Notes 10/26 ^uHALpz56

- Politics in strawberry retail: During times with many strawberries, retailers use disease as an excuse to reject orders => Farmers pay to destroy/ ship back.
- Around 21.07: What does "treating" mean? (treatment is field-wide)
- Ask Katrina to change the scope to pivot to crown rot & provide preliminary data
- Other modalities for early detection
- Tractors doing farm spray can affect the camera rig
- A camera to cover 4 plants ^CHo6WoHK

- Symptoms start at the bottom of plant due to trapped moisture
- Anthracnose: start on fruit's surface, discoloration of the flower,
spores spread via rain dropping on a colony 
- Disease develop faster => Autonomous onboard removal? ^tjpHL4uy

- Can you use a mobile device to disrupt the condition to prevent the disease from developing? ^s9AfS3gS

At least once, ideally twice weekly ^24uPEvBQ

* Capture from 30 min before sunrise to sunset, scheduled by sunrise and sunset times; sleep between captures and at night. Sensors log 24/7.
* Every 15 min, as a 3–5 frame burst; every 5 min in the afternoon and dawn windows if power allows.
* Sensors per system: thermal, RGB, near-infrared camera with a reference panel in view, shaded air temperature and humidity sensor, soil moisture and soil temperature sensor near the crowns.
* 1–2 plants per camera; at least 3 cameras per treatment group, spread across rows.
* Weather-resistant, including dew and condensation control for the lenses and thermal window.
* Clear of tractor spraying; first confirm whether the trial plots get sprayed at all. (Spray on Friday)
* Data stored locally, sized for the full visit interval plus margin.
* Self-powered for the visit interval plus at least 3–4 sunless days.
* Real-time clock, resynced at each visit.
* No manual photos; symptom onset labeled from the time-lapse, plus crown confirmation by culture or PCR at the end.
* Budget: 2k ^3vHo5HNG

Measurements:
- Thermal imaging: Vascular and crown diseases block water flow, which raises leaf temperature before visible symptoms (air temp & humidity readings) ^wwrujoAq

How do I prepare a matrix for CNN training for thermal image? ^4PoMTqjm

Camera System Constraints ^MxriWCbX

Goal: ^O3Yjdr4O

image a single Colletotrichum crown rot species before and after inoculation, as preliminary data ^Z0CTyqdv

Experiment Design ^YQk5J1IM

Cut each crown at the end of the trial and confirm infection by culture or PCR ^Tujj92ho

Pathologists can scroll back through that camera’s time-lapse and mark the first day symptoms were visible ^mOZamSmR

- Scoring each plant on a simple 0–5 wilting scale by staff at GCREC
- Resync real-time clock module regularly ^BDz0JJkl

BOM ^XzfGQHyy

Not plausible
* Daily LoRa status message (battery, storage, frame count, lens sharpness score), or cellular if a thumbnail is needed. ^wbT2AtMH

Faculty ^dRf25Z5c

- Dr. Daeun (Dana) Choi
- Dr. Natalia Peres
- Dr. Nathan Boyd ^7iHcOkpA

Timestamps: with no internet the Pi can’t sync its clock. The CR2032 battery in the RTC holder keeps the clock running. Let the Pi name each file by its own time rather than trusting the camera’s clock. ^XYWenx3k

Questions to ask Xiaomin ^JOFPI7VU

- Is 4 plants a good enough statistical sample? ^PIE3oOCS

split training and test sets by plant, not by image ^O6RkXWwZ

Check & Refocus camera  ^5yRpJdAy

Create a hotspot on the Pi with NetworkManager (nmcli device wifi hotspot ssid <name> password <pw>). The Pi is usually reachable at 10.42.0.1 once your phone connects. ^cXwd02rh

Test the full loop on the bench: capture, view, adjust. ^SfMepaKM

After the field check, turn the hotspot off (for example with nmcli radio wifi off) so it doesn’t draw power or leave an open network all season. Confirm it stays off after a reboot. ^5DhucJ9H

For a quick look, capture a reduced-size frame, which transfers fast, for example rpicam-still -o check.jpg --width 2312 --height 1736. Use the full 9152 × 6944 only for the final focus check. ^UjD1BE4p

Set focus to the crown distance with --lens-position, which is in dioptres (1 ÷ distance in metres). That’s about 0.79 at 1.27 m or about 0.89 at 1.12 m. ^D6EFtIbn

To view the frame on your phone, run python3 -m http.server 8000 in the folder with the images, then open http://10.42.0.1:8000 in the phone’s browser. ^kRJJHUTb

For a live view while you aim, rpicam-vid -t 0 --inline --listen -o tcp://0.0.0.0:8888 --width 1280 --height 960 can be opened in VLC on a laptop. The exact flags depend on Arducam’s driver fork, so confirm them on the bench. ^h8EHLKES

Set up viewing in the lab first ^TaD49cmy

Taking and viewing the check frames ^WDWqzfjM

Build Guide ^U3fGxRam

WAKE_ON_GPIO=0 ^sfcdryjU

-E ^lZpIP1DU

-E ^6EfMBJs8

WAKE_ON_GPIO=0 ^elMWsqdK

For on purpose update, run: sudo apt-mark unhold <names> ^dmeugija

$ sudo apt update && sudo apt full-upgrade
$ sudo reboot ^MaXFVr7Y

Install driver: https://docs.arducam.com/Raspberry-Pi-Camera/Native-camera/64MP-Hawkeye/#afmanual-focus-function ^alRfyZZi

1 ^KtXu6xOE

Fish eye distortion results in higher mm/px near
the edge; roughly double the center => Plants at
edge has lower-resolution & checkerboard to 
straighten the image ^GkF9ukKM

Fish-eye camera ^1Mk1rcsx

Data Backup Routine ^Tq0f8V9Z

- How does the enclosure has to change so I can backup data to 
my laptop via ethernet? ^qoVDQXXj

- We'd need button and external ledDoes ^5BQ00k1t

Train & Test ^Z8mawgmP

- Split train and test by plant, not by frame. ^xHzrNZ2h

Next Iteration ^DiesH9QN

Dataset Design ^mXWb8dqb

1. Group frames into 1 deployment (installation -> remove for spray)
2. Split train & test by plant/ deployment
3. cam0 at t pairs with cam1 at t+30 s, and the pair is dropped if either frame is missing
4. Keep meta.jsonl as raw log and build curated manifest
 ^hmJHIGVH

1. Group frames into scenes, using deployments as the scene.
uScenes groups 95,834 observations into 110 scenes, which belong to 39 collection tasks across 7 field sessions. Each scene has its own folder and a global index records metadata per scene. Your natural scene is one deployment: from reinstall (fuse in, Monday) to removal (fuse out, Thursday). Every reinstall moves the camera slightly, so a deployment is the longest stretch in which the camera geometry stays constant. That gives about 20 deployments per station over the season. Scenes also give you the split unit: frames a minute apart are near-duplicates, so splitting at random by frame leaks data between train and test. Split by plant or by deployment instead. uScenes doesn't describe its splits, but this structure is what makes a clean split possible.

2. A matching rule with an explicit tolerance, plus reported statistics (their Eq. 1).
They match each sonar frame to the nearest camera frame, accept the match only if it is within 83 ms (half the slower sensor's interval), and report the mean, median and 95th-percentile gaps. You need the same rule in three places:
- cam0 ↔ cam1 → one plot-level observation. The cameras fire at :00 and :30, so the tolerance is 30 s (half the interval). Write the rule down: cam0 at t pairs with cam1 at t+30 s, and the pair is dropped if either frame is missing.
- Frames ↔ weather. If you use FAWN 15-minute data, the tolerance is ±7.5 min. I believe FAWN's Balm station is at GCREC, but please check that.
- Frames ↔ disease ratings. This is the most important join. Ratings are weekly and frames are per minute, so state how labels spread across the gap between ratings (nearest rating, last rating carried forward, or interpolation) and flag the frames that fall in between.

3. Two levels of manifest.
uScenes has a JSONL manifest per scene (timestamps, time difference, frame ID, return count) and a separate global scene index (session, duration, description). You already write meta.jsonl raw log and build a curated manifest on the laptop from it:

crownrot/
  index/deployments.jsonl   # station, deploy_id, start/end UTC, treatment, cam height, notes
  index/plants.jsonl        # plant_id, station, flag colour, inoculation date, cultivar
  ratings/ratings.csv       # date, plant_id, severity, rater, scale version
  calib/<deploy_id>/        # colour checker, marker frames, homography
  scenes/<station>_<deploy_id>/                        mani file,exposure, gain, sun_elev, days_after_inoc, pair_id, ...
      cam0/  cam1/                                
4. In-situ calibration, with the calibration       ptures s
- They calibrated the camera intrinsics underwater so the mwaterinterface. Your camera shoots through the IP6box's cl role.Calibrate through the lid, not on the bench.
- They treat the camera–sonar transform as fixebecause  ↔ cam1transform is fixed per frame build, but the camera-to-bed transform changes at every reinstall. Put a few markers (for example ArUco tags) at fixed spots on the bed and estimate homograp corners.They used EPnP plus refinement; RANSAC on thecorners ry frame of the season into one plot coordinate frame, soeach playou getper-plant time series, which early detection needs. The bed top is domed and plants stand about 23the bedplane is approximate. It's fine for crops, not for measurement.
- They recorded dedicated calibration sequences.     For you,d and ascale reference at each install would let you      check coson.
                                                   5. Documenicitly.
They document the coordinate frame and even the    sign flip . Yourequivalents: which way is north and along the row in each image, any rotation or flip per camera,    which halfrs,UTC-only filenames, and what exposure_capped means.
                                                   6. Coarse se.
Their scene classes are explicitly "not            frame-levelish classbalance including a 42% "None" class (Table III).  The same cinoculatedis not the same as symptomatic on a given day. Keep three label levels separate and say which one each file
- treatment, known by design from the flag colour;
- per-plant severity over time, from weekly ratings;
- per-frame boxes or masks, added later.        
Publish a table of counts by treatment × week × verity.
                                                 Honest imitationssection.
They normalise signal per frame and warn that   lues can Do theopposite: your fixed white balance and capped exposure exist so frames can be compared across ys. Keep exposuremetadata, and never normalise per frame in the released data. Their limitations section (one   te, one s to yours: one site, one season, likely one cultivar, and a nadir view while the target user holds a phone at an angle. A small handheld-phone test set would measure that gap.                               
8. A comparison table that positions the datasetheir Tab
Useful columns: in-field vs lab, crown vs       af/fruitgitudinal(same plant over time), fixed viewpoint,        vironmengainststrawberry and general plant-disease datasets.
                                                at doesn

- Building point clouds from sonar and the multimodal fusion that motivates the paper. Yohave two twosensing modalities.                           Their renoevaluation protocol, so it gives no help with rating pt gap.Agree a severity scale and rating schedule with the pathologist before symptoms start in late December

The highest-value items for you now are probably 1, 4 and 6. Items 1 and 6 cost nothing and lock in the struct on thebed before the next reinstall, because deployments that have ers can'tbe registered later. ^vGvG11M4

FAWN is the Florida Automated Weather Network, a set of weather stations across the state run by UF/IFAS. Each station records a reading every 15 minutes:
- air temperature at several heights (60 cm, 2 m, 10 m)
- soil temperature
- relative humidity and dew point
- rainfall
- wind speed and direction
- solar radiation

The data is free to download from the FAWN website. I believe the Balm station is at GCREC, but check that it's close to your bed.

For your dataset it gives you weather covariates per frame. C. gloeosporioides favours warm, humid weather, so temperature and humidity help explain when symptoms appear. Rain and solar radiation help explain what a frame looks like (wet foliage, harsh sun). Weather comes every 15 minutes and you have a frame every minute. So each frame takes the nearest weather reading, and the gap can be at most ±7.5 minutes (half the 15-minute interval). That is the same rule uScenes uses for its camera–sonar matching.

Spreading labels between ratings

Disease ratings are weekly and frames come every minute. Most frames are taken between two ratings and have no rating of their own, so you need a written rule for what label they get.

Example: plant P3, rated on a 0–5 scale:

┌───────┬────────┐
│ Date  │ Rating │
├───────┼────────┤
│ Dec 1 │ 0      │
├───────┼────────┤
│ Dec 8 │ 2      │
└───────┴────────┘

Symptoms sDec 1 andDec 8, but you don't know when. A frame from Dec 4 could be labelled in several ways:

Rule: Near
Dec 4 frame gets: 0 (Dec 1 is closer)
Problem: Sint, Dec
  4–5, a date with no meaning
───────────
Rule: Last rating carried forward
Dec 4 fram
Problem: Labels early-symptom frames as healthy,
  and those are exactly the frames early detection

  is about
────────────────────────────────────────
Rule: Next rating carried backward
Dec 4 frame gets: 2
Problem: Ltoms as
  diseased
───────────
Rule: Linear interpolation
Dec 4 fram
Problem: Assumes steady progression. Crown rot can
  collapseftendoesn't
   progress steadily

None of thsecond half of the advice matters: flag the frames whose
label is a each frame a label_source:
- rated: fhis is aconfident label.
- between_s agree(e.g. 0 and 0). Also confident, because there was no change to miss.
- between_ngs differ(0 → 2). The label is uncertain. Keep these frames out of the test set, and either leave
  them out with lower weight.

Store prevdate oneach frame too, so the rule can be changed later without rebuilding the dataset.                   
A rule that suits early detection: label backwards from onset. Once the season is over, define onset for each plant as the first rating above 0. Then label every frame by days to onset (−10, −5, −1,  0, +3…). Tes intoexactly what you want: pictures of plants 3, 5 or 10 days bes. Onset is only known to within one rating interval, so    ting twives thatuncertainty. Agree that with the pathologist before symptoms start in late December.         
Handoff edit
                                                made twohandoffs/Autonomous_Data_Collecting.md:
- Line 23 (Computer): removed "clear lid facing down". Iut throughthe lid. The Pi is still described as inside the sealed IP67 box.                                - Line 24 ra is notin any enclosure: it sits outside the Pi's box, in open air, with no window in front of the       lens.
- Line 95 (Heat): now says the Pi is in a sealed box in sun and the camera is in open air, also    in sun.

This changes two things from my earlier answer:
- Drop "calibrate through the lid". With no window in front of the lens, a normal lens calibration is enough.
- An open lens brings new image problems: dew,      rain drocts and sun flare. Dew matters most, because your capture window starts at sunrise − 60 min, exactly when   dew formty flag tothe dataset (e.g. clean / dew / droplets / flare), and wipe the lens at every visit and      reinstal

The design spec (docs/superpowers/specs/2026-11-04-crowncam-nly thePi's box, not the camera's position, so I left it unchanged. open-lensproblems added to the handoff's open items. ^AXIrwUV3

%%
## Drawing
```compressed-json
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=
```
%%