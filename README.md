import random
import string

def genera_codice(lunghezza=8):
    """Genera un codice alfanumerico casuale.

    Args:
        lunghezza: La lunghezza del codice (default: 8).

    Returns:
        Una stringa contenente il codice generato.
    """
    caratteri = string.ascii_uppercase + string.digits  # Lettere maiuscole e numeri
    codice = ''.join(random.choice(caratteri) for _ in range(lunghezza))
    return codice

# Esempio di utilizzo:
codice_utente = genera_codice(12)  # Genera un codice di 12 caratteri
print(f"Codice generato: {codice_utente}")

# Esempio di generazione di più codici
num_codici = 5
codici_generati = [genera_codice() for _ in range(num_codici)]
print(f"Codici generati: {codici_generati}")
