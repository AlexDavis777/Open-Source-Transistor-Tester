# Paste this string into your command line and hit enter:

sudo avrdude -c usbasp -P usb -p m644p -B 20 \ -V -U flash:w:./ComponentTester.hex:a -U eeprom:w:./ComponentTester.eep:a

No, the hex doesn't include fuse settings. But you could use avrdude to set the fuses if required (actually just for a brand new ATmega).

sudo avrdude -c usbasp -P usb -p m644p -B 20 \ -V -U flash:w:./ComponentTester.hex:a -U eeprom:w:./ComponentTester.eep:a -U lfuse:w:0xF7:m -U hfuse:w:0xD9:m -U efuse:w:0xfc:m

If the ATmega already runs a tester firmware you don't need to re-write the fuses.

LCD module:
 *  ILI9342
 *  - SPI interface using hardware SPI
 */

//#if 0
#define LCD_ILI9341                     /* display controller ILI9341/ILI9342 */
#define LCD_GRAPHIC                     /* graphic display */
#define LCD_COLOR                       /* color display */
#define LCD_SPI                         /* SPI interface */
/* control and data lines */
#define LCD_PORT         PORTB          /* port data register */
#define LCD_DDR          DDRB           /* port data direction register */
#define LCD_RES          PB2            /* port pin used for /RES (optional) */
//#define LCD_CS           PB4            /* port pin used for /CS (optional) */
#define LCD_DC           PB3            /* port pin used for D/C */
#define LCD_SCK          PB7            /* port pin used for SCK */
#define LCD_SDI          PB5            /* port pin used for SDI (data input) */
//#define LCD_SDO          PB6            /* port pin used for SDO (data output) */
/* display settings */
#define LCD_DOTS_X       320            /* number of horizontal dots */
#define LCD_DOTS_Y       240            /* number of vertical dots */
//#define LCD_FLIP_X                      /* enable horizontal flip */
//#define LCD_FLIP_Y                      /* enable vertical flip */
//#define LCD_ROTATE                      /* switch X and Y (rotate by 90) */
//#define LCD_BGR                         /* reverse red and blue color channels */
//#define LCD_EXT_CMD_OFF                 /* extended commands disabled */
/* font and symbols: horizontally aligned & flipped */
#define FONT_16X26_HF                   /* 16x26 font */
//#define FONT_16X26_ISO8859_2_HF         /* 16x26 Central European font */
//#define FONT_16X26_WIN1251_HF           /* 16x26 cyrillic font */
//#define SYMBOLS_32X32_HF                /* 32x32 symbols */
//#define SYMBOLS_32X32_ALT1_HF           /* 32x32 alternative symbols #1 */
#define SYMBOLS_32X32_ALT2_HF           /* 32x32 alternative symbols #2 */
//#define SYMBOLS_32X39_HF                /* 32x39 symbols */
/* SPI bus */
#define SPI_HARDWARE                    /* hardware SPI */
//#endif

