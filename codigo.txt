import sys
import os
import signal

try:
    from colorama import Fore, Style, init
except ImportError:
    import subprocess
    subprocess.check_call([sys.executable, "-m", "pip", "install", "colorama"])
    from colorama import Fore, Style, init

init()

class TerminalManager:
    def __enter__(self):
        self.original_sigint = signal.getsignal(signal.SIGINT)
        if os.name == 'nt':
            import msvcrt
            self.getch = lambda: msvcrt.getch().decode('latin-1')
        else:
            import tty
            import termios
            self.fd = sys.stdin.fileno()
            self.old_settings = termios.tcgetattr(self.fd)
            tty.setraw(self.fd)
            self.getch = lambda: sys.stdin.read(1)
        return self

    def __exit__(self, *args):
        if os.name != 'nt':
            import termios
            termios.tcsetattr(self.fd, termios.TCSADRAIN, self.old_settings)
        signal.signal(signal.SIGINT, self.original_sigint)
        print(Style.RESET_ALL, end='')

def cargar_codigo():
    try:
        with open('codigo.txt', 'r', encoding='utf-8') as f:
            return f.read()
    except FileNotFoundError:
        print(Fore.RED + "\nERROR: Archivo 'codigo.txt' no encontrado")
        print(Fore.YELLOW + "Crea el archivo con el código a mostrar y vuelve a intentarlo")
        sys.exit(1)
    except Exception as e:
        print(Fore.RED + f"\nERROR AL LEER ARCHIVO: {str(e)}")
        sys.exit(1)

def main():
    def salir():
        print(Style.RESET_ALL + "\n\n" + Fore.RED + "Programa detenido")
        sys.exit(0)

    CODIGO = cargar_codigo()
    
    print(Fore.GREEN + "\n¡Escribe el código con cualquier tecla!")
    print(Fore.YELLOW + "[Ctrl+C para salir]" + Fore.RESET)

    with TerminalManager() as term:
        signal.signal(signal.SIGINT, lambda s, f: salir())
        
        sys.stdout.write(Fore.GREEN)
        sys.stdout.flush()

        term.getch()
        
        for char in CODIGO:
            if term.getch() == '\x03':
                salir()
            
            if char == '\n':
                sys.stdout.write('\n\r')
            elif char == '\t':
                sys.stdout.write('    ')
            else:
                sys.stdout.write(char)
            sys.stdout.flush()

        print(Style.RESET_ALL + "\n\n" + Fore.CYAN + "¡Código cargado completamente! 🚀")

if __name__ == '__main__':
    main()
