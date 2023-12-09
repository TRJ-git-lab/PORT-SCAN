import streamlit as st
import socket

def portlari_tara(hedef_host, baslangic_port, bitis_port):
    st.subheader("TRJ Port SCANNER")

    acik_portlar = []

    for port in range(baslangic_port, bitis_port + 1):
        soket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        soket.settimeout(1)

        sonuc = soket.connect_ex((hedef_host, port))

        if sonuc == 0:
            acik_portlar.append(port)
            st.success(f"Port {port} acik")

        soket.close()

    if not acik_portlar:
        st.warning("Herhangi bir acik port bulunamadi.")

    return acik_portlar

def ana_program():
    st.title("TRJ Port SCANNER")

    

    hedef_host = st.text_input("Hedef Host Girin (Örneğin: 88.232.3.165)", "localhost")
    baslangic_port = st.number_input("Baslangic Portu Girin", min_value=1, max_value=65535, value=1)
    bitis_port = st.number_input("Bitis Portu Girin", min_value=baslangic_port, max_value=65535, value=2000)

    if st.button("Portlari Tara"):
        acik_portlar = portlari_tara(hedef_host, baslangic_port, bitis_port)
        st.subheader("Acik Portlar:")
        st.write(acik_portlar)

if __name__ == "__main__":
    ana_program()
