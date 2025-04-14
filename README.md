# CBT270
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. 
Due to amazing work by Alison Zhang and Jake Choi repos are no longer deleted.

```
//***FILE 270 IS FROM THE WASHINGTON STATE DP SERVICE CENTER AND    *   FILE 270
//*          CONTAINS MANY OF THEIR LOCAL UTILITIES.  THIS FILE IS  *   FILE 270
//*          IN IEBUPDTE SYSIN FORMAT.  FOR ADDITIONAL INFORMATION  *   FILE 270
//*          SEE THE MEMBER CALLED $DOC.                            *   FILE 270
//*                                                                 *   FILE 270
//*          UNFORTUNATELY, OUR DEAR FRIEND KERMIT KISER HAS        *   FILE 270
//*          PASSED ON.  WE MISS HIM GREATLY.                       *   FILE 270
//*                                                                 *   FILE 270
//*          MUCH OF THIS STUFF IS FROM THE MID-1980'S, BUT IT      *   FILE 270
//*          STILL WORKS, OR IT IS CLOSE TO BEING MADE TO WORK.     *   FILE 270
//*                                                                 *   FILE 270
//*          PROBLEMS WITH CONVERTING SOME OF THESE PROGRAMS TO     *   FILE 270
//*          RECENT Z/OS SYSTEMS:                                   *   FILE 270
//*                                                                 *   FILE 270
//*          1.  3390 DISK PACKS WEREN'T INVENTED YET.              *   FILE 270
//*          2.  UCB LOOKUP METHODS HAVE CHANGED.                   *   FILE 270
//*              ETC.                                               *   FILE 270
//*                                                                 *   FILE 270
//*          WE MAY FIND MORE ISSUES BECAUSE OF THE AGE OF THESE    *   FILE 270
//*          PROGRAMS.  IF YOU WANT TO MAKE ANY OF THEM WORK, AND   *   FILE 270
//*          YOU CAN DO IT YOURSELF, PLEASE SEND THE CODE TO SAM    *   FILE 270
//*          GOLOB, TO MAKE THE LATER VERSION KNOWN TO EVERYBODY.   *   FILE 270
//*          OTHERWISE, IF YOU NEED HELP ON CONVERTING ONE OR       *   FILE 270
//*          MORE OF THE PROGRAMS.......                            *   FILE 270
//*                                                                 *   FILE 270
//*          FOR SUPPORT, PLEASE CONTACT SAM GOLOB:                 *   FILE 270
//*                                                                 *   FILE 270
//*             EMAIL:  SBGOLOB@CBTTAPE.ORG                         *   FILE 270
//*                                                                 *   FILE 270
//*          ANY MEMBERS WITH SBGOLOB AS THE ISPF USERID, WERE      *   FILE 270
//*          LOOKED AT, OR MODIFIED, BY SAM GOLOB, AND THEY VERY    *   FILE 270
//*          PROBABLY DO WORK, BUT AT THE PRESENT TIME, THEY ARE    *   FILE 270
//*          FEW (BUT USEFUL - SEE MEMBER COMMANDR).                *   FILE 270
//*                                                                 *   FILE 270
//*             THE PURPOSE OF THIS FILE IS TO TRANSFER SOME OF     *   FILE 270
//*           WDPSC'S LOCAL UTILITIES.  ALL THIS STUFF WORKS HERE,  *   FILE 270
//*           BUT WE DON'T GUARANTEE IT TO WORK ANYWHERE ELSE.      *   FILE 270
//*           SOME PROGRAMS MAY NEED MODIFICATION FOR AN            *   FILE 270
//*           INSTALLATION.  SOME ARE GOOD ONLY AS "HOW TO"         *   FILE 270
//*           SAMPLES.                                              *   FILE 270
//*                                                                 *   FILE 270
//*             THIS FILE CONTAINS THE WDPSC PROGRAMS WHICH WERE    *   FILE 270
//*           PREVIOUSLY IN CBT FILES 270-274.  TWO OF THOSE        *   FILE 270
//*           PROGRAMS, NAMED FTL AND KOMM, HAVE BEEN MODIFIED      *   FILE 270
//*           AND THE LATEST VERSIONS ARE ON THIS TAPE.             *   FILE 270
//*                                                                 *   FILE 270
//*             WE DO HAVE TSO EXTENSIONS AND XA.  ALL OF THE       *   FILE 270
//*           CODE HAS BEEN MODIFIED FOR THIS LEVEL.                *   FILE 270
//*                                                                 *   FILE 270
//*           (KERMIT SAYS MOST OF THE STUFF SEEMS TO WORK ON       *   FILE 270
//*           ESA V3 AND PROBABLY V4.  SOME PROGRAMS MAY HAVE       *   FILE 270
//*           TO BE MODIFIED IF YOU ARE RUNNING SWA ABOVE THE       *   FILE 270
//*           LINE. - SG  1/94)                                     *   FILE 270
//*                                                                 *   FILE 270
//*             MANY OF THE TSO COMMANDS USE THE SETVAR             *   FILE 270
//*           SUBROUTINE.  YOU WILL NEED TO ASSEMBLE SETVAR         *   FILE 270
//*           BEFORE THESE COMMANDS WILL WORK CORRECTLY, THIS       *   FILE 270
//*           PROGRAM IS LINKED WITH AN IBM MODULE.                 *   FILE 270
//*                                                                 *   FILE 270
//*             IF A UTILITY HAS DOCUMENTATION WHICH IS             *   FILE 270
//*           MAINTAINED SEPARATELY, THE DOCUMENT IS IN THE         *   FILE 270
//*           SOURCE PDS WITH A SIMILIAR NAME BUT ENDING WITH THE   *   FILE 270
//*           "$" CHARACTER.                                        *   FILE 270
//*                                                                 *   FILE 270
//*          TO CREATE THE NECESSARY MACLIB, CLIST, PROCLIB, ETC.   *   FILE 270
//*              LIBRARIES:  MODIFY AND SUBMIT EITHER MEMBER        *   FILE 270
//*              REDIST OR REDISTI WHICH ARE IN THIS LIBRARY.       *   FILE 270
//*              (USE REDIST IF PROGRAM PDSLOAD FROM THE CBT TAPE   *   FILE 270
//*              IS AVAILABLE, ELSE USE JOB REDISTI.)  REDIST OR    *   FILE 270
//*              REDISTI WILL CREATE THE MACLIB, CLIST, PROCLIB,    *   FILE 270
//*              PANELS, SKELS, MESSAGES, TEXT, AND PARM            *   FILE 270
//*              LIBRARIES FROM THE APPROPRIATE MEMBERS IN THIS     *   FILE 270
//*              LIBRARY.                                           *   FILE 270
//*                                                                 *   FILE 270
//*          THE CLISTS MEMBER HAD A LOT OF UNNECESSARY BLANK       *   FILE 270
//*              LINES IN THEM.  I MADE AN ATTEMPT TO ELIMINATE     *   FILE 270
//*              THEM.  IF YOU WANT TO SEE THE ORIGINALS, PLEASE    *   FILE 270
//*              GO BACK TO AN EARLIER VERSION OF THIS TAPE, ON     *   FILE 270
//*              FILE 270 (VERSION 507 OR BEFORE) - SBG 09/24       *   FILE 270
//*                                                                 *   FILE 270
//*         NAME       TYPE      DESCRIPTION                        *   FILE 270
//*                                                                 *   FILE 270
//*         OSVTOC     JCL       CONVERT A DASD TO AN OS VTOC       *   FILE 270
//*         IXVTOC               CONVERT A DASD TO INDEXED VTOC     *   FILE 270
//*                                                                 *   FILE 270
//*                    THESE JOBS ARE PROBABLY REQUIRED IF YOU      *   FILE 270
//*                    RUN EITHER THE ENQ1DSN OR SUPRNAME PROGRAMS. *   FILE 270
//*                    IF THE PACK HAS AN INDEXED VTOC INITIALLY,   *   FILE 270
//*                    IT IS BEST TO RUN JOB OSVTOC TO CONVERI IT   *   FILE 270
//*                    TO AN OS VTOC, THEN RUN ENQ1DSN OR SUPRNAME, *   FILE 270
//*                    AND THEN USE JOB IXVTOC TO CONVERT IT BACK   *   FILE 270
//*                    TO AN INDEXED PACK. (PRESERVES FREE SPACE.)  *   FILE 270
//*                                                                 *   FILE 270
//*         $CHGLOG    DOCUMENT  LOG OF CHANGES AND ADDITIONS       *   FILE 270
//*                              TO THE MODS FILE.                  *   FILE 270
//*                                                                 *   FILE 270
//*         ALLOCGDG   PROGRAM   DYNAMICALLY ALLOCATE A GDG         *   FILE 270
//*                              DATASET TO A DDNAME BASED ON       *   FILE 270
//*                              RELATIVE GENERATION NUMBER         *   FILE 270
//*                              (BECAUSE TSO ALLOC WILL NOT        *   FILE 270
//*                              DO IT!).                           *   FILE 270
//*                                                                 *   FILE 270
//*         ALLOCMEM   PROGRAM   DYNAMICALLY ALLOCATE A             *   FILE 270
//*                              PARTITIONED DATASET AND ITS        *   FILE 270
//*                              MEMBER TO A GIVEN DDNAME           *   FILE 270
//*                              FROM A HIGH LEVEL LANGUAGE         *   FILE 270
//*                              PROGRAM.                           *   FILE 270
//*                                                                 *   FILE 270
//*         CATBYVOL   PROGRAM   CHECKS IDCAMS UNCATALOG CARDS      *   FILE 270
//*                              CREATED BY VSAMSCAN PROGRAM        *   FILE 270
//*                              AGAINST VOLUMES TO FIND NVSAM      *   FILE 270
//*                              DATASETS WHICH DO NOT EXIST.       *   FILE 270
//*                              SEE JOB IN CATBYVO#.  I THINK      *   FILE 270
//*                              DYL260 STEP IS NOT NEEDED.         *   FILE 270
//*                                                                 *   FILE 270
//*         CHKBLOCK   PROGRAM   BATCH PROGRAM TO SCAN JCL OR       *   FILE 270
//*                              PROCS AND REPORT ON OUTPUT         *   FILE 270
//*                              DATASETS NOT EFFICIENTLY           *   FILE 270
//*                              BLOCKED.  SAMPLE JCL IN            *   FILE 270
//*                              CHKBLOC# WILL SCAN A LIBRARY.      *   FILE 270
//*                                                                 *   FILE 270
//*         CHKTODAY   PROGRAM   BATCH PROGRAM TO CHECK FOR         *   FILE 270
//*                              EXISTENCE AND CURRENCY OF A        *   FILE 270
//*                              DATASET.  SETS A RETURN CODE.      *   FILE 270
//*                              WE USE SO THAT ONLY THE FIRST      *   FILE 270
//*                              CALLER OF OUR DAILY VOLUME         *   FILE 270
//*                              REPORT PROCESS ON ANY DAY          *   FILE 270
//*                              DOES THE EXTENSIVE ANALYSIS        *   FILE 270
//*                              OF ALL VOLUMES.                    *   FILE 270
//*                                                                 *   FILE 270
//*         CLIB       CLIST     ALLOCATE A PRIVATE CLIST           *   FILE 270
//*                              LIBRARY FOR IMPLICIT CLIST         *   FILE 270
//*                              EXECUTION WITHOUT REMOVING         *   FILE 270
//*                              PREVIOUSLY ALLOCATED CLIST         *   FILE 270
//*                              LIBRARIES.  USES COMMAND           *   FILE 270
//*                              CONCATEM.                          *   FILE 270
//*                                                                 *   FILE 270
//*         CLRSPFIO   PROGRAM   CAN BE CALLED DIRECTLY OR          *   FILE 270
//*                              LINKED TO DYNAMICALLY VIA THE      *   FILE 270
//*                              ISPEXEC SELECT PGM(CLRSPFIO)       *   FILE 270
//*                              TO TELL SPF TO IGNORE ANY          *   FILE 270
//*                              NON-SPF IO WHICH MAY HAVE          *   FILE 270
//*                              TAKEN PLACE IN THE DIALOG.         *   FILE 270
//*                              NOW ALLOWS PARM OPTIONS FOR        *   FILE 270
//*                              MORE COMPLEX REQUIREMENTS.         *   FILE 270
//*                              THE FOLLOWING SEQUENCE KILLED      *   FILE 270
//*                              THE SCREEN OVERFLOW WHEN           *   FILE 270
//*                              EXITING RESOLVE CONSOLE MODE       *   FILE 270
//*                              TO ISPF:                           *   FILE 270
//*                                                                 *   FILE 270
//*                       ISPEXEC SELECT PGM(CLRSPFIO) PARM(OFF)    *   FILE 270
//*                       ISPEXEC SELECT PGM(CLRSPFIO) PARM(INIT)   *   FILE 270
//*                       ISPEXEC SELECT PGM(CLRSPFIO) PARM(NORM)   *   FILE 270
//*                                                                 *   FILE 270
//*         CMDOUT     CLIST     UTILITY CLIST USED BY CLISTS       *   FILE 270
//*                              AND DIALOGS TO ALLOCATE AND        *   FILE 270
//*                              FREE WORK FILES.  USES             *   FILE 270
//*                              COMMANDS IFALC AND FILEINFO.       *   FILE 270
//*                                                                 *   FILE 270
//*         CNTLCRT    PROGRAM   CAN BE CALLED BY CLISTS TO         *   FILE 270
//*                              ISSUE CNTL OR FULLSCR TPUT         *   FILE 270
//*                              MESSAGES.                          *   FILE 270
//*                                                                 *   FILE 270
//*         CNV2GREG   PROGRAM   THIS IS A SUBROUTINE WHICH         *   FILE 270
//*                              WILL RETURN A FORMATTED            *   FILE 270
//*                              GREGORIAN DATE GIVEN A             *   FILE 270
//*                              STANDARD DATE, JULIAN DATE OR      *   FILE 270
//*                              SERIAL DATE.                       *   FILE 270
//*                                                                 *   FILE 270
//*         COMMANDR   PROGRAM   AUTHORIZED PROGRAM TO TAKE A       *   FILE 270
//*                              COMMAND FROM THE PARM FIELD        *   FILE 270
//*                              AND ISSUE IT VIA SVC 34.           *   FILE 270
//*                                                                 *   FILE 270
//*         CONCATEM   TSO CMD   ALLOCATE OR DEALLOCATE,            *   FILE 270
//*         (CONCAT)             CONCATENATE OR DECONCATENATE       *   FILE 270
//*                              THE GIVEN DATASET TO THE           *   FILE 270
//*                              GIVEN DDNAME.  IN THE CASE OF      *   FILE 270
//*                              CONCATENATION, PLACE THE           *   FILE 270
//*                              GIVEN DATASET "AT THE TOP OF       *   FILE 270
//*                              THE STACK" OF ALL DATASETS         *   FILE 270
//*                              CONCATENATED TO THAT DDNAME.       *   FILE 270
//*                                                                 *   FILE 270
//*         CRY        PROGRAM   ISPF EDIT MACRO TO ENCRYPT         *   FILE 270
//*                              AND DECRYPT DATA BY CALLING        *   FILE 270
//*                              R050A90 PGM FROM CBT TAPE.         *   FILE 270
//*                              INVOKED BY ENCRYPT & DECRYPT       *   FILE 270
//*                              CLIST MACROS.                      *   FILE 270
//*                                                                 *   FILE 270
//*         CTLGTMS#   JCL       CHECKS IDCAMS UNCATALOG CARDS      *   FILE 270
//*                              CREATED BY VSAMSCAN PROGRAM        *   FILE 270
//*                              AGAINST TMS TMC TO FIND NVSAM      *   FILE 270
//*                              DATASETS WHICH DO NOT EXIST.       *   FILE 270
//*                              IF DYL260 IS NOT AVAILABLE,        *   FILE 270
//*                              SOME CONVERSION IS NEEDED.         *   FILE 270
//*                                                                 *   FILE 270
//*         DATECONV   TSO CMD   ACCEPT A STANDARD, JULIAN, OR      *   FILE 270
//*                              SERIAL DATE AND THEN CONVERT       *   FILE 270
//*                              IT TO THE OTHER TWO.               *   FILE 270
//*                                                                 *   FILE 270
//*         DDNTODSN   PROGRAM   SUBROUTINE CALLED BY PROGRAMS      *   FILE 270
//*                              TO RETURN DSNAME AND VOLSER        *   FILE 270
//*                              BASED ON DDNAME PASSED.            *   FILE 270
//*                                                                 *   FILE 270
//*         DEVTYPE    TSO CMD   DETERMINE DEVICE TYPE GIVEN        *   FILE 270
//*                              VOLUME SERIAL NUMBER.              *   FILE 270
//*                                                                 *   FILE 270
//*         DOCSYS     .......   THIS IS AN ISPF DIALOG SYSTEM      *   FILE 270
//*                              FOR ONLINE MANAGEMENT AND          *   FILE 270
//*                              RETRIEVAL OF DOCUMENTS.  IT        *   FILE 270
//*                              USES MANY OF THE OTHER             *   FILE 270
//*                              UTILITIES ON THIS TAPE.  SEE       *   FILE 270
//*                              MEMBER DOCSYS$ FOR MORE            *   FILE 270
//*                              DETAILS.                           *   FILE 270
//*                                                                 *   FILE 270
//*         DSN        CLIST &   DISPLAY DATASET ENQS VIA DSNQ      *   FILE 270
//*                    TSO CMD   CMD, A VERSION OF DENQ (SEE        *   FILE 270
//*                              ENQ1DSN, ENQ1LOAD, ENQ2LOAD        *   FILE 270
//*                              SOURCE).  THESE ARE XA             *   FILE 270
//*                              VERSIONS WITH GQSCAN SUPPORT.      *   FILE 270
//*                                                                 *   FILE 270
//*         DSNTAB     PROGRAM   SUBROUTINE TO PASS BACK LIST       *   FILE 270
//*                              OF ALL DSNAMES CONCATENATED        *   FILE 270
//*                              TO A GIVEN DDNAME.                 *   FILE 270
//*                                                                 *   FILE 270
//*         DUMPVOL    PROGRAM   A SAMPLE PROGRAM WHICH READS       *   FILE 270
//*                              A LIST OF VOLUMES AND BUILDS       *   FILE 270
//*                              A JOB TO DUMP (FDR) ONLY           *   FILE 270
//*                              THOSE VOLUMES WHICH ARE            *   FILE 270
//*                              CURRENTLY MOUNTED.  NO MORE        *   FILE 270
//*                              DOES DUANE HAVE TO COME IN AT      *   FILE 270
//*                              3 AM BECAUSE SOME VOLUMES ARE      *   FILE 270
//*                              NOT MOUNTED.                       *   FILE 270
//*                                                                 *   FILE 270
//*         DYNALLOC   PROGRAM   SUBROUTINE TO DYNAMICALLY          *   FILE 270
//*                              ALLOCATE A GIVEN DATASET TO A      *   FILE 270
//*                              GIVEN DDNAME.                      *   FILE 270
//*                                                                 *   FILE 270
//*         EDITNEW    DIALOG    ISPF/PDF REPLACEMENT EDIT          *   FILE 270
//*         EDITAPP              (OPTION 2) DIALOGS.  ALLOWS        *   FILE 270
//*                              SAVING LISTS OF DATASETS TO        *   FILE 270
//*                              SELECT FROM FOR EDITING OR         *   FILE 270
//*                              BROWSING.  SEE EDIT$ FOR           *   FILE 270
//*                              DETAILS.                           *   FILE 270
//*                                                                 *   FILE 270
//*         FILEATTR   PROGRAM   OBTAIN VOLUME SERIAL NUMBER,       *   FILE 270
//*                              LRECL, BLKSIZE, DSORG, RECORD      *   FILE 270
//*                              FORMAT, AND DEVICE TYPE OF         *   FILE 270
//*                              DATASET GIVEN THE DATASET          *   FILE 270
//*                              NAME (AND VOLUME SERIAL            *   FILE 270
//*                              NUMBER IF NOT CATALOGED) FROM      *   FILE 270
//*                              A HIGH LEVEL LANGUAGE PGM.         *   FILE 270
//*                                                                 *   FILE 270
//*         FILEINFO   TSO CMD   RETURN INFO TO A CLIST SUCH        *   FILE 270
//*                              AS LRECL, BLKSIZE, RECFM,          *   FILE 270
//*                              DSORG, VOLSER, ETC.                *   FILE 270
//*                                                                 *   FILE 270
//*         FILSPACE   PROGRAM   SUBROUTINE THAT ACCEPTS A          *   FILE 270
//*                              DATASET NAME AND VOLUME            *   FILE 270
//*                              SERIAL NUMBER AND RETURNS THE      *   FILE 270
//*                              NUMBER OF USED EXTENTS AND         *   FILE 270
//*                              THE NUMBER OF USED TRACKS.         *   FILE 270
//*                                                                 *   FILE 270
//*         FINDMEM    PROGRAM   DETERMINE WHETHER A SPECIFIED      *   FILE 270
//*                              MEMBER OF A PDS EXISTS OR NOT.     *   FILE 270
//*                                                                 *   FILE 270
//*         FINDTTR    PROGRAM   CALLED BY THE FINDTTR CLIST        *   FILE 270
//*                              TO SEARCH A PDS FOR A GIVEN        *   FILE 270
//*                              STRING.  THE TTR OF ALL BLOCKS     *   FILE 270
//*                              CONTAINING THE STRING IS           *   FILE 270
//*                              DISPLAYED WHETHER IN               *   FILE 270
//*                              DIRECTORY, MEMBERS, GAS, OR        *   FILE 270
//*                              BEYOND DS1LSTAR.                   *   FILE 270
//*                                                                 *   FILE 270
//*         FIREUP     CLIST     ALLOCATE USER SPF DIALOG           *   FILE 270
//*                              MANAGER LIBRARIES AHEAD OF         *   FILE 270
//*                              THE SPF PROGRAM DEVELOPMENT        *   FILE 270
//*                              FACILITY LIBRARIES AND/OR TO       *   FILE 270
//*                              ALLOCATE LIBRARIES TO DIALOG       *   FILE 270
//*                              MANAGER DDNAMES NOT ALREADY        *   FILE 270
//*                              ALLOCATED.                         *   FILE 270
//*                                                                 *   FILE 270
//*         FTL        PROGRAM   IEBGENER REPLACEMENT FOR           *   FILE 270
//*                              COPYING FILES.  HANDLES            *   FILE 270
//*                              MULTIPLE FILES, CHANGING DCB       *   FILE 270
//*                              CHARACTERISTICS, MOST FILE         *   FILE 270
//*                              TYPES.                             *   FILE 270
//*                                                                 *   FILE 270
//*         GDDM       MISC.     OUR INTERFACE TO GDDM AND PGF      *   FILE 270
//*                              UTILITIES.  PANELS - GDDM,         *   FILE 270
//*                              GDDMR3H                            *   FILE 270
//*                                                                 *   FILE 270
//*                              CLISTS - CHART,IMD,ISSE,LPQ,VSSE   *   FILE 270
//*                                                                 *   FILE 270
//*                              LOADMODS-                          *   FILE 270
//*                                IFALC,DATASTAT,KOMM,DEVTYPE,     *   FILE 270
//*                                FILEINFO                         *   FILE 270
//*                                NEWWAIT,ADMUSP6,LISTMEMS,LPRTQ,  *   FILE 270
//*                                PROGDQUE                         *   FILE 270
//*                                                                 *   FILE 270
//*                              SOURCE - DATASTAT,ADMUSP6,         *   FILE 270
//*                              ADMUSP6O,LPRTQ2,PROGDQ             *   FILE 270
//*                                                                 *   FILE 270
//*                              DOCS - CHART,GDDM,ISSE,            *   FILE 270
//*                              SAMPSYMS,VSSE                      *   FILE 270
//*                                                                 *   FILE 270
//*                              JCL - PROGDQ#                      *   FILE 270
//*                                                                 *   FILE 270
//*                     NOTE:    ADMUSP6 IS ENHANCED IBM            *   FILE 270
//*                              SAMPLE PGM TO LOAD DATA INTO       *   FILE 270
//*                              ICU.  PROGDQUE BUILDS GDDM         *   FILE 270
//*                              QUEUE.  LPRTQ DISPLAYS             *   FILE 270
//*                              CONTENTS OF GDDM QUEUE.            *   FILE 270
//*                              ADMUSP6B IS BATCH CHART            *   FILE 270
//*                              UTILITY.                           *   FILE 270
//*                                                                 *   FILE 270
//*         GETMY      TSO CMD   SAMPLE COMMAND FOR RETURNING       *   FILE 270
//*                              USER/SYSTEM DATA TO CLIST          *   FILE 270
//*                              VARIABLES.  SOME INSTALLATION      *   FILE 270
//*                              SENSITIVE CODE, BUT A GOOD         *   FILE 270
//*                              STARTING PLACE!                    *   FILE 270
//*                                                                 *   FILE 270
//*         HEXTRAN    PROGRAM   TRANSLATE DATA FROM CHARACTER      *   FILE 270
//*                              CODED HEXADECIMAL TO TRUE          *   FILE 270
//*                              HEXADECIMAL OR VICE VERSA.         *   FILE 270
//*                                                                 *   FILE 270
//*         HOSEDOWN   CLIST     DEALLOCATE USER SPF DIALOG         *   FILE 270
//*                              MANAGER LIBRARIES (UNDO WHAT       *   FILE 270
//*                              A PREVIOUS FIREUP DID).            *   FILE 270
//*                                                                 *   FILE 270
//*         HOTKEYS    CLISTS    SETS PFKS TO CALL HOTKEY           *   FILE 270
//*                              CLIST AS NESTED ISPF DIALOG.       *   FILE 270
//*                              HOTKEY CLIST EXTRACTS DATASET      *   FILE 270
//*                              NAME (SEE ISPCDSN PROGRAM) AT      *   FILE 270
//*                              CURSOR LOCATION AND CALLS THE      *   FILE 270
//*                              REQUESTED APPLICATION (PDS         *   FILE 270
//*                              CMD, BROWSE, EDIT, ETC.)           *   FILE 270
//*                              PASSING THE DATASET NAME!          *   FILE 270
//*                              ALSO SUPPORTS DDNAMES AND VIO      *   FILE 270
//*                              DSNAMES.                           *   FILE 270
//*                                                                 *   FILE 270
//*         IFALC      TSO CMD   TESTS WHETHER A GIVEN DDNAME       *   FILE 270
//*                              OR DSNAME IS CURRENTLY             *   FILE 270
//*                              ALLOCATED TO THE USER.             *   FILE 270
//*                                                                 *   FILE 270
//*         IFCAT      TSO CMD   TESTS WHETHER A GIVEN DSNAME       *   FILE 270
//*                              IS CATALOGED.  FILEINFO GIVES      *   FILE 270
//*                              BETTER DATA.                       *   FILE 270
//*                                                                 *   FILE 270
//*         IKJUPDT    PROGRAM   SUBROUTINE TO CONVERT CALLS        *   FILE 270
//*                              TO IKJUPDT INTO LINK TO            *   FILE 270
//*                              PROGRAM SETVAR.  WE USED TO        *   FILE 270
//*                              LINK IBM IKJUPDT (IKJCT433)        *   FILE 270
//*                              DIRECTLY WITH TSO COMMANDS IN      *   FILE 270
//*                              ORDER TO PUT DATA INTO CLIST       *   FILE 270
//*                              VARIABLES.  THIS TECHNIQUE IS      *   FILE 270
//*                              MUCH MORE MAINTAINABLE!.           *   FILE 270
//*                                                                 *   FILE 270
//*         INDEX      PROGRAM   TO SCAN A STRING FOR A             *   FILE 270
//*                              DELIMITER AND SET A RETURN         *   FILE 270
//*                              CODE BASED ON ITS LOCATION -       *   FILE 270
//*                              USED BY HOTKEYS CLIST.  SETS       *   FILE 270
//*                              RC=0 IF NOT FOUND.                 *   FILE 270
//*                                                                 *   FILE 270
//*         INMRZ01    PROGRAM   TSO/E RECEIVE COMMAND EXIT.        *   FILE 270
//*                              INTERFACES WITH ACF2 TO            *   FILE 270
//*                              CONTROL USERID ACCESS AND          *   FILE 270
//*                              ALLOW BATCH RECEIVE.  MODIFY       *   FILE 270
//*                              THE SPOOL MAINTENENCE JOB          *   FILE 270
//*                              CHECK SECTION FOR YOUR             *   FILE 270
//*                              INSTALLATION.                      *   FILE 270
//*                                                                 *   FILE 270
//*         INTRDR     PROGRAM   THIS PROGRAM WILL ACCEPT A         *   FILE 270
//*                              DDNAME PASSED TO IT IN THE         *   FILE 270
//*                              PARAMETER LIST AND THEN            *   FILE 270
//*                              DYNAMICALLY ALLOCATE THE           *   FILE 270
//*                              INTERNAL READER TO THAT            *   FILE 270
//*                              DDNAME.                            *   FILE 270
//*                                                                 *   FILE 270
//*         ISPCDSN    PROGRAM   FANTASTIC PROGRAM TO EXTRACT       *   FILE 270
//*                              A DATASET NAME FROM THE LAST       *   FILE 270
//*                              DISPLAYED PANEL IF THE CURSOR      *   FILE 270
//*                              WAS PLACED ANYWHERE ON A           *   FILE 270
//*                              DATASET NAME AND PUT IT IN AN      *   FILE 270
//*                              ISPF VARIABLE!  PLEASE DON'T       *   FILE 270
//*                              TELL IBM ABOUT THIS ONE - IT       *   FILE 270
//*                              USES SOME INTERNAL ISPF            *   FILE 270
//*                              POINTERS THAT WE AREN'T            *   FILE 270
//*                              SUPPOSED TO KNOW ABOUT!            *   FILE 270
//*                                                                 *   FILE 270
//*         ISPCMDS    TABLE     ISPF COMMAND TABLE WE USE.         *   FILE 270
//*                              ALLOWS A DIALOG OR PANEL TO        *   FILE 270
//*                              OVERRIDE COMMANDS, MAP PFKS,       *   FILE 270
//*                              ACTIVATE SCROLL KEYS, ETC BY       *   FILE 270
//*                              JUST SETTING A FUNCTION            *   FILE 270
//*                              VARIABLE.  EFFECT IS LOCAL AND     *   FILE 270
//*                              DOES NOT SCREW UP YOUR SPLIT       *   FILE 270
//*                              SCREENS.  ALSO HAS RTSO, OPT,      *   FILE 270
//*                              BR, ED COMMAND SUPPORT FOR         *   FILE 270
//*                              NESTING FUNCTIONS.                 *   FILE 270
//*                                                                 *   FILE 270
//*         ISPF       MISC      ISR*PRIM,KMENU,SPFBATU...          *   FILE 270
//*                              VARIOUS ISPF STUFF TO SHOW         *   FILE 270
//*                              HOW WE HOOK IT ALL TOGETHER        *   FILE 270
//*                              HERE.  TRACE INVISIBLE OPTION      *   FILE 270
//*                              'K' TO FIND IT.                    *   FILE 270
//*                                                                 *   FILE 270
//*         ISPFMACS   CLISTS    CUT/PASTE, CENTER, SHOWFLOW,       *   FILE 270
//*                              COM ARE ISPF EDIT MACROS.          *   FILE 270
//*                              SOME CONVERTED FROM IBM            *   FILE 270
//*                              DISKETTE FOR TSO.  SORRY, NO       *   FILE 270
//*                              DOCS AVAILABLE, BUT SOME HELP      *   FILE 270
//*                              PANELS.  (CUTHELP,PASTEHLP)        *   FILE 270
//*                                                                 *   FILE 270
//*         JCLXREF    PROC      THIS PROCEDURE READS A             *   FILE 270
//*                              PROCEDURE LIBRARY AND/OR JOB       *   FILE 270
//*                              STREAMS AND OUTPUTS UP TO SIX      *   FILE 270
//*                              REPORTS.  CROSS REFERENCE          *   FILE 270
//*                              PROGRAMS AND DATASET NAMES         *   FILE 270
//*                              WITH PROCEDURE NAMES AND           *   FILE 270
//*                              THEIR STEP NAMES.  USES            *   FILE 270
//*                              DYL260.                            *   FILE 270
//*                                                                 *   FILE 270
//*         JTOSCONV   PROGRAM   CONVERT JULIAN DATES OF THE        *   FILE 270
//*                              FORM YYDDD TO STANDARD             *   FILE 270
//*                              (MMDDYY) AFTER DATE                *   FILE 270
//*                              VALIDATION.                        *   FILE 270
//*                                                                 *   FILE 270
//*         KOMM       TSO CMD   COMMAND TO DO SIMPLE 3270 IO       *   FILE 270
//*                              FROM A CLIST, SUCH AS CLEAR        *   FILE 270
//*                              THE SCREEN OR FORMAT FIELDS.       *   FILE 270
//*                                                                 *   FILE 270
//*         LASTLINK   CLIST     DISPLAY INFORMATION ABOUT THE      *   FILE 270
//*                              LAST TIME A COBOL OR               *   FILE 270
//*                              ASSEMBLER PROGRAM WAS              *   FILE 270
//*                              COMPILED AND LINKED.               *   FILE 270
//*                                                                 *   FILE 270
//*         LISTMEMS   PROGRAM   GIVEN THE NAME OF A                *   FILE 270
//*                              PARTITIONED DATA SET, PRODUCE      *   FILE 270
//*                              AN OUTPUT FILE WHOSE RECORDS       *   FILE 270
//*                              CONTAIN THE NAMES OF THE           *   FILE 270
//*                              MEMBERS OF THAT PDS (ONE           *   FILE 270
//*                              RECORD PER MEMBER).                *   FILE 270
//*                                                                 *   FILE 270
//*         LOADXREF   PROC      CROSS REFERENCE CALLING            *   FILE 270
//*                              PROGRAMS TO CALLED PROGRAM         *   FILE 270
//*                              AND VICE VERSA.  (USES             *   FILE 270
//*                              SHIFT90, A 90 DEGREE PRINT         *   FILE 270
//*                              PROGRAM.  IF YOU DO NOT HAVE       *   FILE 270
//*                              THIS OR IBM'S ROTATE90, THERE      *   FILE 270
//*                              IS A PUBLIC DOMAIN 90 DEGREE       *   FILE 270
//*                              PGM IN FILE 316, CBT MODS          *   FILE 270
//*                              TAPE).                             *   FILE 270
//*                                                                 *   FILE 270
//*         LOCATE     TSO CMD   FROM THE CBT TAPE ORIGINALLY.      *   FILE 270
//*                              MODIFIED TO USE LPALST00 AS        *   FILE 270
//*                              WELL AS LNKLST00 ON AN XA          *   FILE 270
//*                              SYSTEM.  SUPPORTS                  *   FILE 270
//*                              CONCATENATED STEPLIBS ALSO.        *   FILE 270
//*                              NOW HAS ISPLLIB SUPPORT AND        *   FILE 270
//*                              DOES MULTI-MEMBERS OK.             *   FILE 270
//*                                                                 *   FILE 270
//*         LOGKILLR   PROGRAM   AN OLD PROGRAM DESIGNED TO         *   FILE 270
//*                              KILL TSO LOGON ADDRESS SPACES      *   FILE 270
//*                              WHICH HANG IN THE USER-PROMPT      *   FILE 270
//*                              CODE DUE TO USER WALKING           *   FILE 270
//*                              AWAY, ETC.                         *   FILE 270
//*                                                                 *   FILE 270
//*         MEMSTAT    TSO CMD   CHECKS A PDS FOR A MEMBER AND      *   FILE 270
//*                              SETS &LASTCC.  YEAH, I KNOW        *   FILE 270
//*                              THERE ARE MANY, BUT WPPSS          *   FILE 270
//*                              WANTS...                           *   FILE 270
//*                                                                 *   FILE 270
//*         MLPALIST   PROGRAM   LISTS MODULES LOADED BY MLPA       *   FILE 270
//*                              OR FLPA.  SIMILIAR TO AMBLIST      *   FILE 270
//*                              LISTLPA.                           *   FILE 270
//*                                                                 *   FILE 270
//*         NEWISPF    PROGRAM   THIS MODULE IS THE FRONTEND        *   FILE 270
//*                              FOR ISPF AND/OR PDF.  IT HAS       *   FILE 270
//*                              THE FOLLOWING FUNCTIONS:           *   FILE 270
//*                                                                 *   FILE 270
//*                           1. SAVE THE INPUT ECT BECAUSE         *   FILE 270
//*                              ISPF MODIFIES THE ECT PTR TO       *   FILE 270
//*                              THE IOWA WHICH IS NEEDED BY        *   FILE 270
//*                              THE WDPSCXS MODULE FOR             *   FILE 270
//*                              STACKING COMMANDS.                 *   FILE 270
//*                                                                 *   FILE 270
//*                           2. ALLOCATE THE USER PROFILE LIB      *   FILE 270
//*                              TO DDNAME ISPPROF.                 *   FILE 270
//*                                                                 *   FILE 270
//*                           3. INVOKE THE NEWSPF CLIST IF         *   FILE 270
//*                              PROFILE LIB DOESN'T EXIST.         *   FILE 270
//*                              NEWSPF CREATES NEW USER            *   FILE 270
//*                              PROFILES.                          *   FILE 270
//*                                                                 *   FILE 270
//*                           4. CALL THE REAL ISPF OR PDF          *   FILE 270
//*                              COMMAND MODULE.                    *   FILE 270
//*                                                                 *   FILE 270
//*         NEWMWILE   PROGRAM   ATTACHES ITSELF, THEN              *   FILE 270
//*                              TERMINATES.  SELECTED USERS        *   FILE 270
//*                              INVOKE THIS PROGRAM WHEN THEY      *   FILE 270
//*                              START AN ISPF SESSION TO           *   FILE 270
//*                              BECOME EXEMPT FROM THE 522         *   FILE 270
//*                              ABENDS WHICH WE FORCE ON THE       *   FILE 270
//*                              AVERAGE USER.  USES REUSABLE       *   FILE 270
//*                              MODULE ITCOMA1.                    *   FILE 270
//*                                                                 *   FILE 270
//*         NEWWAIT    PROGRAM   WAIT FOR A SPECIFIED PERIOD        *   FILE 270
//*                              OF TIME WITHOUT USING CPU          *   FILE 270
//*                              TIME.  THIS IS THE                 *   FILE 270
//*                              INTERRUPTIBLE VERSION OF           *   FILE 270
//*                              WAITER.                            *   FILE 270
//*                                                                 *   FILE 270
//*         NEXTGEN    TSO CMD   RETURN TWO CLIST                   *   FILE 270
//*                              VARIABLES  &CURGEN  AND            *   FILE 270
//*                              &NXTGEN  WHERE  &CURGEN            *   FILE 270
//*                              CONTAINS  THE  ABSOLUTE            *   FILE 270
//*                              GENERATION NUMBER OF THE +0        *   FILE 270
//*                              GENERATION AND &NXTGEN             *   FILE 270
//*                              CONTAINS  THE  ABSOLUTE            *   FILE 270
//*                              GENERATION NUMBER OF THE +1        *   FILE 270
//*                              GENERATION FOR A GDG.              *   FILE 270
//*                                                                 *   FILE 270
//*         PACKLIST   PROGRAM   UTILITY TO BUILD IEAPAK00          *   FILE 270
//*                              FROM DATA PRODUCED BY PSWSAMP      *   FILE 270
//*                              ROUTINE.                           *   FILE 270
//*                                                                 *   FILE 270
//*         PSWSAMP    PROGRAM   TRACE TABLE SAMPLING UTILITY       *   FILE 270
//*                              FOR PRODUCING DATA USED BY         *   FILE 270
//*                              PACKLIST PROGRAM.                  *   FILE 270
//*                                                                 *   FILE 270
//*         REPROENQ   PROGRAM   PROGRAM TO ENQ ON SYSIGGV2         *   FILE 270
//*                              FOR A CATALOG ALLOCATED TO         *   FILE 270
//*                              STEPLIB AND CALL IDCAMS.  CAN      *   FILE 270
//*                              BACKUP THE CATALOGS WITHOUT        *   FILE 270
//*                              CODING DISP=OLD AND DRAINING       *   FILE 270
//*                              THE SYSTEM USING THIS.  SEE        *   FILE 270
//*                              REPROEN#.                          *   FILE 270
//*                                                                 *   FILE 270
//*         RJETRANS   PROGRAM   REASSEMBLE RECORDS THAT HAVE       *   FILE 270
//*                    (DYL280)  BEEN TRANSMITTED AS 80 BYTE        *   FILE 270
//*                              SEGMENTS VIA RJE TO THEIR          *   FILE 270
//*                              ORIGINAL LOGICAL RECORD LENGTH.    *   FILE 270
//*                                                                 *   FILE 270
//*         RTSO       PROGRAM   RTSO IMPLEMENTS A "REMEMBER        *   FILE 270
//*                              LAST TSO COMMAND" FUNCTION FOR     *   FILE 270
//*                              BOTH THE "TSO" COMMAND ON THE      *   FILE 270
//*                              "COMMAND ==>" AND FOR THE TSO      *   FILE 270
//*                              COMMAND PANEL, PRIMARY MENU        *   FILE 270
//*                              OPTION.  THE TSO COMMAND PANEL     *   FILE 270
//*                              CAN BE BROUGHT UP FROM ANYWHERE    *   FILE 270
//*                              BY ENTERING "TSO" WITHOUT AN       *   FILE 270
//*                              OPERAND, JUST LIKE THE "KEYS"      *   FILE 270
//*                              COMMAND.  THE LAST COMMAND         *   FILE 270
//*                              ENTERED MAY BE PRESENTED WHEN      *   FILE 270
//*                              THE TSO COMMAND PANEL IS           *   FILE 270
//*                              DISPLAY RELATED:  PANELS           *   FILE 270
//*                              ISRTSO,SPFEOPT,SPFEOH; CLIST       *   FILE 270
//*                              SPFEOPT; CMD TABLE ISPCMDS         *   FILE 270
//*                                                                 *   FILE 270
//*         SCXSCAN    PROGRAM   LINKS AS A FRONT-END TO            *   FILE 270
//*                              IKJSCAN TO PROVIDE AN "X CMD"      *   FILE 270
//*                              FACILITY FROM ANY SUBCOMMAND       *   FILE 270
//*                              MODE USING IKJSCAN (JUST LIKE      *   FILE 270
//*                              PCF X FACILITY)                    *   FILE 270
//*                                                                 *   FILE 270
//*         SERLCONV   PROGRAM   CONVERT SERIAL DATES TO            *   FILE 270
//*                              STANDARD DATE FORMAT AFTER         *   FILE 270
//*                              DATE VALIDATION.                   *   FILE 270
//*                                                                 *   FILE 270
//*         SETRC      PROGRAM   THIS PROGRAM TURNS A PARM          *   FILE 270
//*                              FIELD INTO A CONDITION CODE.       *   FILE 270
//*                              IT IS USED TO CONTROL              *   FILE 270
//*                              EXECUTION OF PROC STEPS BASED      *   FILE 270
//*                              ON PARMS SPECIFIED.  NOT AS        *   FILE 270
//*                              GOOD AS A NEW JCL LANGUAGE,        *   FILE 270
//*                              BUT A START.                       *   FILE 270
//*                                                                 *   FILE 270
//*         SETVAR     PROGRAM   THIS IS A SUBROUTINE WHICH A       *   FILE 270
//*                              TSO COMMAND CAN LINK TO IN         *   FILE 270
//*                              ORDER TO SET A CLIST               *   FILE 270
//*                              VARIABLE.  IT LINKS IN             *   FILE 270
//*                              IKJCT433(IKJUPDT) FROM LPALIB      *   FILE 270
//*                              FOR PRE TSO/E SYSTEMS. FOR         *   FILE 270
//*                              TSO/E SYSTEMS, THE NEW             *   FILE 270
//*                              IKJCT441 TSO/E INTERFACE IS        *   FILE 270
//*                              USED.                              *   FILE 270
//*                                                                 *   FILE 270
//*         SHOW       TSO CMD   REPLACEMENT FOR JTIP SHOW ALL      *   FILE 270
//*                              COMMAND. REQUIRES JES2             *   FILE 270
//*                              EXIT-22, XJ22SHOW, AND             *   FILE 270
//*                              IGC00236 (INCLUDED).               *   FILE 270
//*                                                                 *   FILE 270
//*         SPACE      TSO CMD   DISPLAYS ALLOCATION,               *   FILE 270
//*                              UTILIZATION AND EXTENT INFO        *   FILE 270
//*                              FOR A DATASET.  CAN RETURN         *   FILE 270
//*                              DATA TO A CLIST.                   *   FILE 270
//*                                                                 *   FILE 270
//*         SMF64EXT   PROGRAM   ANALYZES SMF TYPE 64 RECORDS       *   FILE 270
//*                              TO IDENTIFY VSAM DATASETS          *   FILE 270
//*                              WHICH ARE GOOD CANDIDATES FOR      *   FILE 270
//*                              USE ON CACHED DISK VOLUMES.        *   FILE 270
//*                                                                 *   FILE 270
//*         SMF74MOD   PROGRAM   MERGES SMF TYPE 74 RECORDS         *   FILE 270
//*                              FROM MULTIPLE CPUS SO              *   FILE 270
//*                              ERBRMFPP DEVICE ACTIVITY           *   FILE 270
//*                              REPORT WILL SHOW ALL ACTIVITY      *   FILE 270
//*                              TO SHARED DEVICES.  WORKS FOR      *   FILE 270
//*                              XA AND NON-XA MIXTURES ALSO.       *   FILE 270
//*                                                                 *   FILE 270
//*         SMPEIOF    PROGRAM   INTERCEPTS SMP/E CALLS TO TSO      *   FILE 270
//*                              STATUS COMMAND AND REROUTES        *   FILE 270
//*                              THEM TO STATUS CLIST               *   FILE 270
//*                              (INCLUDED) WHICH USES IOF TO       *   FILE 270
//*                              CHECK STATUS AND DISPLAY SMP/E     *   FILE 270
//*                              JOBS.  MUCH BETTER THAN TSO        *   FILE 270
//*                              OUTPUT COMMAND.                    *   FILE 270
//*                                                                 *   FILE 270
//*         SPFCATNV   CLIST     THIS IS AN ISPF DIALOG FOR         *   FILE 270
//*                              DOING NVSAM CATALOG                *   FILE 270
//*                              FUNCTIONS.  WE USE IT AS TECH      *   FILE 270
//*                              SERVICES OPTION K.N HERE.          *   FILE 270
//*                              GOOD IF YOU HAVE MULTIPLE          *   FILE 270
//*                              MASTER AND USER CATALOGS LIKE      *   FILE 270
//*                              WE DO.  CHANGE CAT NAMES IN        *   FILE 270
//*                              THE CLIST.                         *   FILE 270
//*                                                                 *   FILE 270
//*         PANLEXIT   PROGRAM   ISPF DIALOG INTERFACE TO           *   FILE 270
//*                              ALLOW EXITS FROM ISPF DISPLAY      *   FILE 270
//*                              PANELS (NOT SELECT PANELS          *   FILE 270
//*                              YET) TO A DIALOG OR ISPF SERVICE.  *   FILE 270
//*                              (REPLACED BY SPFEXEC.)             *   FILE 270
//*                                                                 *   FILE 270
//*         SPFEXEC    PROGRAM   ISPF DIALOG INTERFACE TO           *   FILE 270
//*         (PANLEXIT)           ALLOW EXITS FROM ISPF              *   FILE 270
//*                              DISPLAY PANELS (NOT SELECT         *   FILE 270
//*                              PANELS) TO A DIALOG OR ISPF        *   FILE 270
//*                              SERVICE.  THIS IS A                *   FILE 270
//*                              REPLACEMENT FOR PANLEXIT.  IT      *   FILE 270
//*                              IS ONE OF OUR BEST MODS!  IT       *   FILE 270
//*                              ALLOWS FANTASTIC FLEXIBILITY       *   FILE 270
//*                              IN MODIFYING VENDOR DIALOGS,       *   FILE 270
//*                              ETC.  IT ALSO PROVIDES THE         *   FILE 270
//*                              INTERFACES TO ISPLINK WHICH        *   FILE 270
//*                              IBM FORGOT!  IT CAN BE CALLED      *   FILE 270
//*                              AS A REAL TSO COMMAND IN           *   FILE 270
//*                              CONTRAST TO ISPEXEC WHICH          *   FILE 270
//*                              WON'T WORK FROM FOCUS, SAS,        *   FILE 270
//*                              ETC.  IT CAN ALSO BE CALLED        *   FILE 270
//*                              DIRECTLY WITH A SINGLE             *   FILE 270
//*                              ISPEXEC PARM STRING IN             *   FILE 270
//*                              CONTRAST TO THE TWO PARMS          *   FILE 270
//*                              (LENGTH,STRING) ISPLINK            *   FILE 270
//*                              REQUIRES.  IT ACCEPTS MORE         *   FILE 270
//*                              FLEXIBLE OPTIONS THAN ISPEXEC      *   FILE 270
//*                              AND WILL EVEN INITIALIZE ISPF      *   FILE 270
//*                              IF NEEDED!!!                       *   FILE 270
//*                                                                 *   FILE 270
//*                       SOME SYNTAX EXAMPLES:                     *   FILE 270
//*                            SPFEXEC SELECT PANEL(ISRUTIL)        *   FILE 270
//*                       OR   SPFEXEC PANEL(ISRUTIL)               *   FILE 270
//*                            SPFEXEC 3.1                          *   FILE 270
//*                       OR   * SPFEXEC 'PANEL(ISRUTIL) OPT(1)'    *   FILE 270
//*                            ETC., ETC., ETC........              *   FILE 270
//*                                                                 *   FILE 270
//*         SPFPRINT   PROGRAM   THIS IS LINKED AS A FRONT END      *   FILE 270
//*                              FOR YOUR DSPRINT COMMAND.  IT      *   FILE 270
//*                              PICKS UP AN ISPF VARIABLE AND      *   FILE 270
//*                              ADDS THE CONTENTS TO THE           *   FILE 270
//*                              COMMAND PASSED BY ISPF.  NOW       *   FILE 270
//*                              YOU CAN MODIFY THE DSPRINT         *   FILE 270
//*                              COMMANDS ISSUED BY ISPF.  DOES     *   FILE 270
//*                              NOT AFFECT NORMAL DSPRINT          *   FILE 270
//*                              REQUESTS.                          *   FILE 270
//*                                                                 *   FILE 270
//*         STACK      TSO CMD   STACK IS A NORMAL TSO COMMAND      *   FILE 270
//*                                    PROCESSOR:  STACK -          *   FILE 270
//*                                    DDIN(INPUTDD) -              *   FILE 270
//*                                    DDOUT(OUTDD) -               *   FILE 270
//*                                    TASKLIB(TASKDD) LIST         *   FILE 270
//*                                                                 *   FILE 270
//*                              INPUTDD - DDNAME TO READ           *   FILE 270
//*                                        COMMAND FROM             *   FILE 270
//*                                        INSTEAD OF NORMAL        *   FILE 270
//*                                        SOURCE                   *   FILE 270
//*                                                                 *   FILE 270
//*                              OUTDD   - DDNAME THE COMMAND       *   FILE 270
//*                                        OUTPUT SHOULD GO TO      *   FILE 270
//*                                                                 *   FILE 270
//*                              TASKDD  - DDNAME THE COMMAND       *   FILE 270
//*                                        SHOULD BE ATTACHED       *   FILE 270
//*                                        FROM IF DESIRED          *   FILE 270
//*                                                                 *   FILE 270
//*                              LIST    - MEANS DISPLAY THE        *   FILE 270
//*                                        COMMAND ON THE           *   FILE 270
//*                                        OUTPUT FILE              *   FILE 270
//*                                                                 *   FILE 270
//*                              (ALL OPERANDS ARE OPTIONAL)        *   FILE 270
//*                              (ALL FILE I/O MUST BE DONE         *   FILE 270
//*                              VIA PUTGET MODULE TO BE            *   FILE 270
//*                              INTERCEPTED).                      *   FILE 270
//*                                                                 *   FILE 270
//*         STOJCONV   PROGRAM   CONVERT STANDARD DATES OF THE      *   FILE 270
//*                              FORM (MMDDYY) TO JULIAN AND        *   FILE 270
//*                              SERIAL AFTER DATE VALIDATION.      *   FILE 270
//*                                                                 *   FILE 270
//*         SUPRNAME   PROGRAM   THE SUPRNAME PROGRAM IS A          *   FILE 270
//*                              FRONT END PROCESSOR TO             *   FILE 270
//*                              AMASPZAP WHICH ADDS SOME NEW       *   FILE 270
//*                              CONTROL CARDS TO THE SUPERZAP      *   FILE 270
//*                              VANILLA CARDS.  IT ALLOWS A        *   FILE 270
//*                              DATASET TO BE RENAMED OR           *   FILE 270
//*                              SCRATCHED WITH NO ENQ              *   FILE 270
//*                              CONTENTION EVEN IF THE             *   FILE 270
//*                              DATASET NAME IS ALLOCATED TO       *   FILE 270
//*                              ANOTHER JOB.  IT ALSO ALLOWS A     *   FILE 270
//*                              FORMAT ONE DSCB TO BE DUMPED       *   FILE 270
//*                              OR ZAPPED WITHOUT KNOWING THE      *   FILE 270
//*                              CCHHR ADDRESS IN THE VTOC.         *   FILE 270
//*                                                                 *   FILE 270
//*         SYSOUT     TSO CMD   COMMAND TO ALLOCATE SYSOUT         *   FILE 270
//*                              FILES USING THE NEW TEXT           *   FILE 270
//*                              UNITS FOR FLASH, CHARS,            *   FILE 270
//*                              MODIFY, ETC.                       *   FILE 270
//*                                                                 *   FILE 270
//*         TERMTYPE   PROGRAM   PROGRAM CAN BE CALLED BY A         *   FILE 270
//*                              CLIST TO DETERMINE SCREEN          *   FILE 270
//*                              LINES, I.E. TERMINAL TYPE -        *   FILE 270
//*                              TTY,M2,M3,ETC.                     *   FILE 270
//*                                                                 *   FILE 270
//*         TIMECOND   PROGRAM   SETS CONDITION CODE TO DAY OF      *   FILE 270
//*                              WEEK, MONTH, YEAR, ETC. FOR        *   FILE 270
//*                              CONDITIONAL EXECUTION OF           *   FILE 270
//*                              STEPS.                             *   FILE 270
//*                                                                 *   FILE 270
//*         TRANS      TSO CMD   TRANSLATES CHARACTERS IN           *   FILE 270
//*                              CLIST VARIABLES.  SEE SOURCE       *   FILE 270
//*                              FOR USE DOCUMENTATION.  NO         *   FILE 270
//*                              HELP MEM YET.                      *   FILE 270
//*                                                                 *   FILE 270
//*         UCBMAP     TSO CMD   A VERSION OF THE UCBMAP            *   FILE 270
//*                              COMMAND FROM FILE 301 OF THE       *   FILE 270
//*                              CBT TAPE WITH XA SUPPORT           *   FILE 270
//*                              (IOSVSUCB).                        *   FILE 270
//*                                                                 *   FILE 270
//*         UCC7MOD    SOURCE    A SOURCE PATCH TO UCC7 MODULE      *   FILE 270
//*                              SASSLGON TO ALLOW ANY VTAM         *   FILE 270
//*                              TERMINAL TO SIGN ON TO UCC7.       *   FILE 270
//*                                                                 *   FILE 270
//*         UNCLIB     CLIST     DEALLOCATE (REMOVE) A PRIVATE      *   FILE 270
//*                              CLIST LIBRARY PREVIOUSLY           *   FILE 270
//*                              ALLOCATED TO YOUR SESSION.         *   FILE 270
//*                                                                 *   FILE 270
//*         UNNUM      CLIST     A CLIST TO REMOVE CLIST LINE       *   FILE 270
//*                              NUMS FOR PRINTING.                 *   FILE 270
//*                                                                 *   FILE 270
//*         VOL2DEVT   PROGRAM   SUBROUTINE TO RETURN               *   FILE 270
//*                              DEVICE TYPE FOR GIVEN VOL.         *   FILE 270
//*                                                                 *   FILE 270
//*         VSAMSCAN   PROGRAM   READS CATALOG AND WRITES           *   FILE 270
//*                              IDCAMS UNCATALOG CARDS FOR         *   FILE 270
//*                              ALL NVSAM DATASETS WHICH ARE       *   FILE 270
//*                              THEN PROCESSED BY PROGRAM          *   FILE 270
//*                              CATBYVOL.  SEE JOB IN              *   FILE 270
//*                              CATBYVO#.  I THINK DYL260 STEP     *   FILE 270
//*                              IS NOT NEEDED.                     *   FILE 270
//*                                                                 *   FILE 270
//*         WATDSN     CLIST     UTILITY TO DIPLAY DATASETS         *   FILE 270
//*                    PROGRAM   ALLOCATED TO A GIVEN DDNAME.       *   FILE 270
//*                                                                 *   FILE 270
//*         WDPSCXS    PROGRAM   SUBROUTINE CALLED BY ISPF          *   FILE 270
//*                              DIALOGS TO STACK A COMMAND         *   FILE 270
//*                              FOR EXECUTION WHEN ISPF            *   FILE 270
//*                              TERMINATES.  USED FOR OUR          *   FILE 270
//*                              OPTION XL (EXIT,LOGOFF).           *   FILE 270
//*                              REQUIRES NEWISPF FRONTEND TO       *   FILE 270
//*                              WORK CORRECTLY.  SEE CLIST         *   FILE 270
//*                              SPFXL AND PANEL ISR*PRIM           *   FILE 270
//*                              ALSO...                            *   FILE 270
//*                                                                 *   FILE 270
//*         WHATDDN    TSO CMD   RETURN TO THE CLIST THE            *   FILE 270
//*                              DDNAME(S) OF THE DATASET(S)        *   FILE 270
//*                              WHICH IS (ARE) ALLOCATED TO        *   FILE 270
//*                              THE DSNAME GIVEN.                  *   FILE 270
//*                                                                 *   FILE 270
//*         WHATDSN    TSO CMD   RETURN TO THE CLIST THE            *   FILE 270
//*                              DSNAME(S) OF THE DATASET(S)        *   FILE 270
//*                              WHICH IS (ARE) ALLOCATED TO        *   FILE 270
//*                              THE DDNAME GIVEN.                  *   FILE 270
//*                                                                 *   FILE 270
//*         WHOISI     CLIST     LIST ATTRIBUTES ABOUT YOUR         *   FILE 270
//*                    DIALOG    LOGONID SUCH AS ACCOUNT            *   FILE 270
//*                              NUMBER, SYSTEM NUMBER, USER        *   FILE 270
//*                              CATALOG, LOGON PROCEDURE,          *   FILE 270
//*                              PROFILE PREFIX, ETC.               *   FILE 270
//*                                                                 *   FILE 270
//*         WTOPARM    PROGRAM   SEND A MESSAGE FROM THE PARM       *   FILE 270
//*                              FIELD TO THE OPERATOR.             *   FILE 270
//*                                                                 *   FILE 270
//*         WTORCOND   PROGRAM   ASK OPERATOR A QUESTION (Y OR      *   FILE 270
//*                              N) AND SET CONDITION CODE FOR      *   FILE 270
//*                              EXECUTION OF LATER STEPS.          *   FILE 270
//*                                                                 *   FILE 270
//*         XEQ        COMMAND   CALLS A PROGRAM FROM A             *   FILE 270
//*                              TASK/STEPLIB OR THE LINKLIST       *   FILE 270
//*                              WITHOUT ALLOCATION OVERHEAD        *   FILE 270
//*                              OF 'CALL'.  KNOWN AS * HERE.       *   FILE 270
//*                                                                 *   FILE 270
```
