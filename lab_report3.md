# **Lab Report #3**
***

## Part 1
***

1.
`{1, 2, 3}`
an array of the numbers 1, 2, and 3 is the failure inducing input which demonstrates there is a bug
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests{
@Test
public void testReverseInPlace(){
  int[] input1 = { 1, 2, 3 };
  ArrayExamples.reverseInPlace(input1);
  assertArrayEquals(new int[] { 3, 2, 1 }, input1);
  }
}
```
2.
`{ 3 }`
an array of the number 3 is the input which does not induce a failure and does not demonstrate there is a bug
```
import static org.junit.Assert.*;
import org.junit.*;

public class ArrayTests {
	@Test 
	public void testReverseInPlace() {
    int[] input1 = { 3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3 }, input1);
	}
}
```
3.
## Test Failed
![TestFailed](lab4a.png)

## Test Passed
![TestPassed](lab4b.png)

4.
## Before
```
public class ArrayExamples {
  
  // Changes the input array to be in reversed order (contains bug)
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
}
```
## After
```
public class ArrayExamples {
  
  // Changes the input array to be in reversed order
  static void reverseInPlace(int[] arr) {
    int arrCopy = new int[arr.length];
    for (int i = 0; i < arrCopy.length; i++){
      arrCopy[i] = arr[i];
    }
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arrCopy[arr.length - i - 1];
    }
  }
}
```
5. We were able to fix this issue by creating a copy of the array and putting this into `arrCopy`. This will fix the issue since we do not replace the second half of the array as there is
a copy and we do not make any changes to the original array. Before the fix, we were trying to copy the values to the second half of the array, but this was not possible since the values in the
first half of the array were no longer the same as they had been changed in the loop, respectively.

## Part 2
***

Note: The `*` at the end of each line is searching through all of the files in the current working directory.

Example 1: `-l` - This command is checking all files to match the pattern but this will only include those that do contain the given keyword within the file itself. This would certainly be useful when needing to find text that contains a specific keyword.

- In this example we are looking for any files which contain `bcr` within the file itself.
```
ericpalafox@Erics-iMac biomed % grep -l "bcr" *      
1471-2164-3-6.txt
ericpalafox@Erics-iMac biomed % 
```

- In this example we are looking for any files which contain `Guiliani` within the file itself.
```
ericpalafox@Erics-iMac 911report % grep -l "Giuliani" *         
chapter-13.5.txt
chapter-9.txt
ericpalafox@Erics-iMac 911report % 
```

Example 2: `-L` - This command is checking all files that do not match the pattern given within the file itself. This would certainly be useful when needing to find text that does not contain a specific keyword.

- In this example we are looking for any files which do not contain `police` within the file itself.
```
ericpalafox@Erics-iMac 911report % grep -L "police" *    
chapter-1.txt
chapter-13.1.txt
chapter-13.2.txt
chapter-2.txt
chapter-5.txt
chapter-8.txt
preface.txt
ericpalafox@Erics-iMac 911report % 
```

- In this example we are looking for any files which do not contain `Virginia` within the file itself.
```
ericpalafox@Erics-iMac 911report % grep -L "Virginia" *
chapter-10.txt
chapter-12.txt
chapter-13.1.txt
chapter-13.2.txt
chapter-2.txt
chapter-5.txt
chapter-8.txt
preface.txt
ericpalafox@Erics-iMac 911report % 
```

Example 3: `-i` - This command will ignore the case sensitivity and will look for the specific keyword within the given location, and will separate each instance of the word by lines. This is certainly useful as we may need to find a particular keyword where case sensitivity is not important and we have a large text for example.

- In this example we are looking for files which contain the string `police`, however, the case sensitivity is not important as `Police` and any other variation will also be found if it is within the files.
```
ericpalafox@Erics-iMac 911report % grep -i "police" chapter-9.txt
                local public servants, especially the first responders: fire, police, emergency
                evacuated from the roof of the South Tower by New York Police Department (NYPD)
                the New York Police Department, the Port Authority Police Department (PAPD), and the
            Port Authority Police Department. On September 11, 2001, the Port Authority of New
                York and New Jersey Police Department consisted of 1,331 officers, many of whom were
            Most Port Authority police commands used ultra-high-frequency radios. Although all
            The New York Police Department.
            The 40,000-officer NYPD was headed by a police commissioner, whose duties were not
            The 11,000-member FDNY was headed by a fire commissioner who, unlike the police
                Authority police desk in 5 WTC, to be activated by members of the Port Authority
                police when the FDNY units responding to the WTC complex so requested. However, in
            Civilians who called the Port Authority police desk located at 5 WTC were advised to
            Several South Tower occupants called the Port Authority police desk in 5 WTC. Some
                working on upper floors. Chiefs also spoke with Port Authority police personnel and
                Authority police officer to evacuate the South Tower, because in their judgment the
                and 800 police officers from all over the city. The Chief of Department arrived at
            The Port Authority's on-site commanding police officer was standing in the concourse
                officers in the WTC Command to meet at the police desk in 5 WTC. Soon thereafter, he
            One Port Authority police officer at the WTC immediately began climbing stairwell C
            Within minutes of impact, Port Authority police officers from the PATH, bridges,
                calamity in the North Tower. This order was given over WTC police radio channel W,
            At 8:59, the Port Authority police desk at Newark Airport told a third party that a
                Port Authority police desk in Jersey City confirmed that employees on the 64th floor
                should "be careful, stay near the stairwells, and wait for the police to come up."
                When the third party inquired again at 9:31, the police desk at Newark Airport
                advised that they "absolutely" evacuate. The third party informed the police desk
                concourse, where other police officers guided them to exit the concourse and complex
                decided to send one ESU team (each with approximately six police officers) up each
            Throughout this period (9:03 to 9:59), a group of NYPD and Port Authority police
            Initial responders from outside PAPD commands proceeded to the police desk in 5 WTC
                police desk reporting at least 100 people trapped.
                9:30, the PAPD central police desk requested that responding officers meet at West
                advised orally to leave the building by other firefighters and police who were
                police officers to descend because they lacked the protective gear and equipment
                needed to handle the increasing smoke and heat. The police officers reluctantly
                teamed up with a Port Authority police officer and acted as a spotter in advising
                of Department, the Port Authority Police Department Superintendent, and many of
                37 fatalities-the largest loss of life of any police force in history. The NYPD
                suffered 23 fatalities-the second largest loss of life of any police force in
            Mayor Giuliani, along with the Police and Fire commissioners and the OEM director,
                Police Academy. Over the coming hours, weeks, and months, thousands of civilians and
                response. Many fire and police agencies that responded had extensive prior
                attack. In addition to county fire, police, and sheriff 's departments, the response
                State Police, the Virginia Department of Emergency Management, the FBI, FEMA, a
                were not (1) fire or police first responders, (2) security or fire safety personnel
                and Police Commissioner consulted with the Chief of the Department of the FDNY at
                complicated by senior Port Authority Police officials becoming directly involved in
                themselves. Although there were ESU teams and a few individual police officers
                command that comprehensively deploys all dispatched police, fire, and other first
            The story with respect to Port Authority police officers in the NorthTower is less
                Authority police evacuation order was given. Since September 11, the Port Authority
ericpalafox@Erics-iMac 911report % 
```

- In this example we are looking for files which contain the string `PATH`, however, the case sensitivity is not important as `path` and any other variation will also be found if it is within the files.
```
ericpalafox@Erics-iMac 911report % grep -i "PATH" * 
chapter-1.txt:    The protocols did not contemplate an intercept. They assumed the fighter escort would be discreet, "vectored to a position five miles directly behind the hijacked aircraft," where it could perform its mission to monitor the aircraft's flight path.
chapter-1.txt:    The controller checked to see if American Airlines could establish communication with American 11. He became even more concerned as its route changed, moving into another sector's airspace. Controllers immediately began to move aircraft out of its path, and asked other aircraft in the vicinity to look for American 11.
chapter-1.txt:    The controller tracking American 77 told us he noticed the aircraft turning to the southwest, and then saw the data disappear. The controller looked for primary radar returns. He searched along the plane's projected flight path and the airspace to the southwest where it had started to turn. No primary targets appeared. He tried the radios, first calling the aircraft directly, then the airline. Again there was nothing. At this point, the Indianapolis controller had no knowledge of the situation in New York. He did not know that other aircraft had been hijacked. He believed American 77 had experienced serious electrical or mechanical failure, or both, and was gone.
chapter-1.txt:    According to the radar reconstruction, American 77 reemerged as a primary target on Indianapolis Center radar scopes at 9:05, east of its last known position. The target remained in Indianapolis Center's airspace for another six minutes, then crossed into the western portion of Washington Center's airspace at 9:10. As Indianapolis Center continued searching for the aircraft, two managers and the controller responsible for American 77 looked to the west and southwest along the flight's projected path, not east-where the aircraft was now heading. Managers did not instruct other controllers at Indianapolis Center to turn on their primary radar coverage to join in the search for American 77.
chapter-1.txt:    Reagan National controllers then vectored an unarmed National Guard C- 130H cargo aircraft, which had just taken off en route to Minnesota, to identify and follow the suspicious aircraft. The C-130H pilot spotted it, identified it as a Boeing 757, attempted to follow its path, and at 9:38, seconds after impact, reported to the control tower:"looks like that aircraft crashed into the Pentagon sir."
chapter-1.txt:    At 9:36, the FAA's Boston Center called NEADS and relayed the discovery about an unidentified aircraft closing in on Washington:"Latest report. Aircraft VFR [visual flight rules] six miles southeast of the White House. . . . Six, southwest. Six, southwest of the White House, deviating away." This startling news prompted the mission crew commander at NEADS to take immediate control of the airspace to clear a flight path for the Langley fighters:"Okay, we're going to turn it . . . crank it up. . . . Run them to the White House." He then discovered, to his surprise, that the Langley fighters were not headed north toward the Baltimore area as instructed, but east over the ocean." I don't care how many windows you break," he said." Damn it. . . . Okay. Push them back."
chapter-1.txt:    At 10:02, the communicators in the shelter began receiving reports from the Secret Service of an inbound aircraft-presumably hijacked-heading toward Washington. That aircraft was United 93. The Secret Service was getting this information directly from the FAA. The FAA may have been tracking the progress of United 93 on a display that showed its projected path to Washington, not its actual radar return. Thus, the Secret Service was relying on projections and was not aware the plane was already down in Pennsylvania.
chapter-10.txt:                    overwhelming international sympathy for the United States.
chapter-11.txt:                20/20 vision. But the path of what happened is so brightly lit that it places
chapter-11.txt:                especially difficult in a transnational case. We sympathize with the working-level
chapter-12.txt:                    about confronting Islamist extremists. Many in the government have sympathized
chapter-12.txt:                were sympathetic to America now perceive the United States as an unfriendly state.
chapter-12.txt:                the Palestinians, with whom Saudis ardently sympathize. Although Saudi Arabia's
chapter-12.txt:                help. Though Saddam Hussein was widely detested, many Saudis are sympathetic to the
chapter-12.txt:                agreements (FTAs) with the Middle Eastern nations most firmly on the path to reform.
chapter-13.2.txt:                11,2001; NTSB report, "Flight Path Study-American Airlines Flight 11," Feb. 19,
chapter-13.2.txt:                11, 2001; NTSB report, "Flight Path Study-American Airlines Flight 11," Feb. 19,
chapter-13.2.txt:            39. NTSB report, "Flight Path Study-American Airlines Flight 11," Feb. 19, 2002.
chapter-13.2.txt:                report,"Flight Path Study-United Airlines 175," Feb. 19,2002; NTSB report,
chapter-13.2.txt:            44. NTSB report, "Flight Path Study-United Airlines 175," Feb. 19, 2002; NTSB report,
chapter-13.2.txt:            47. NTSB report, "Flight Path Study-United Airlines 175," Feb. 19, 2002.
chapter-13.2.txt:            51. NTSB report, "Flight Path Study-United Airlines 175," Feb. 19, 2002.
chapter-13.2.txt:                NTSB report, "Flight Path Study-American Airlines Flight 77," Feb. 19, 2002. Flight
chapter-13.2.txt:                For cruising altitude, see NTSB report,"Flight Path Study-American Airlines Flight
chapter-13.2.txt:                "Flight Path Study-American Airlines Flight 77," Feb. 19, 2002. On American 11, the
chapter-13.2.txt:                September 11, 2001," Sept. 17, 2001; NTSB report, "Flight Path Study-American
chapter-13.2.txt:                17, 2001; NTSB report, "Flight Path Study-American Airlines Flight 77," Feb. 19,
chapter-13.2.txt:            61. See NTSB report, "Flight Path Study-American Airlines Flight 77," Feb. 19, 2002;
chapter-13.2.txt:                maximum speed without regard to overspeed warnings, a straight-line path, and no
chapter-13.3.txt:                School Ties Lead Down Dangerous Paths," CTC 2003- 40028CHX, Mar. 10, 2003.
chapter-13.4.txt:                2004; Feb. 19, 2004; Apr. 3, 2004. For KSM's antipathy to the United States, see
chapter-13.5.txt:                2002). On the scarcity of radios, see PAPD statement 9, PATH Command (Jan. 28,
chapter-13.5.txt:                frequencies, see PANYNJ interview 4 (May 10, 2004); PAPD statement 9, PATH Command
chapter-13.5.txt:                clear path to the stairwell entrance from their locations. Damage caused by the
chapter-2.txt:                the rulers and people who turned away from the true path of their religion, thereby
chapter-2.txt:                leaders who abandoned the pure path of religious devotion.
chapter-2.txt:                by the late 1970s. At the same time, these regimes had closed off nearly all paths
chapter-2.txt:                Among sympathetic peers in Afghanistan were a few of the warlords still fighting for
chapter-5.txt:                followed a rather tortuous path to his eventual membership in al Qaeda.
chapter-5.txt:                persuade Jarrah to depart from "the path he was taking" proved unavailing.101Yet
chapter-5.txt:                Qaeda sympathizers in specific foreign branch offices of large, international
chapter-5.txt:                sympathizers who turned a blind eye to al Qaeda's fundraising activities.
chapter-6.txt:                retracing many of the paths traveled by its predecessors.U.S. envoys again pressed
chapter-7.txt:                sympathetic to those extremist views. During a post-9/11 search of his possessions,
chapter-7.txt:                operatives, eliciting greater donations, and increasing the number of sympathizers
chapter-8.txt:                with or sympathetic to Usama Bin Ladin." Despite the general warnings, the message
chapter-9.txt:                civilians who had been caught in the path of the fireball. Floor-to-ceiling windows
chapter-9.txt:                and in the PATH (Port Authority Trans-Hudson) station below the WTC complex.
chapter-9.txt:            Within minutes of impact, Port Authority police officers from the PATH, bridges,
chapter-9.txt:                evacuation in the plaza, concourse, and PATH station. As information was received of
chapter-9.txt:                the PATH station below the concourse-unaware that the PAPD had cleared the area of
chapter-9.txt:                itself. They used their flashlights to provide a path of beacons through the
chapter-9.txt:                enter the North Tower spread into chain formation and created a path for civilians
chapter-9.txt:                stairs instead of searching for a clear path down, when stairwell A was at least
preface.txt:                enormous sympathy for the victims and their loved ones, and with enhanced respect
ericpalafox@Erics-iMac 911report % 
```


Example 4:

```

```

Sources:

`https://www.freecodecamp.org/news/grep-command-in-linux-usage-options-and-syntax-examples/`
`https://www.geeksforgeeks.org/grep-command-in-unixlinux/`
