# Translation-of-alignment
START

Align sequences in MAFT\ClustalW etc. Save as fasta-file
(Not 'текстовый файл', it should be .fasta and 'все файлы')
DO NOT FORGET for the smallest, reference seq
to insert in the id of "reference seq" word "ref"
Fasta-file should have a path "C:\\Users\\Пользователь\\Desktop\\align.fasta",
in another case change the path in part 1.

In PYTHON shell\PYTHON command line, before you start:
run commands:
import Bio
from Bio.Seq import SeqIO
from Bio.Seq import Seq

You do not need to run it again if you use the same command
line. If you restart the command line, run it again

Run part 1.

part1

for seq_record in SeqIO.parse("C:\\Users\\Пользователь\\Desktop\\align.fasta", "fasta"):
	if str(seq_record.id).find('ref')>=0:
		s1=str(seq_record.seq)
		le=len(s1)
		a=s1.find('A')
		b=s1.find('T')
		c=s1.find('G')
		d=s1.find('C')
		m=min(a,b,c,d)
		s2=s1[::-1]
		a2=s2.find('A')
		b2=s2.find('T')
		c2=s2.find('G')
		d2=s2.find('C')
		m2=min(a2,b2,c2,d2)
		m3=le-m2
	j=str(seq_record.id)
	y='>'
	print(y+j)
	s=str(seq_record.seq)
	print(s[m:m3])

Copy all the sequences and save as fasta (see notes above)
Fasta-file should have a path "C:\\Users\\Пользователь\\Desktop\\cons.fasta",
in another case change the path in part 2.
Run part 2

part 2

w=0
for seq_record in SeqIO.parse("C:\\Users\\Пользователь\\Desktop\\cons.fasta", "fasta"):
			u=str(seq_record.id)
			if u.find('ref')>=0:
				mrna1=str(seq_record.seq)
				mrna1=Seq(mrna1.replace('T','U'))
				mrna1t=str(mrna1.translate())
				if mrna1t.find('*')<0:
					w=w+1
				mrna2=mrna1[1:]
				mrna2t=str(mrna2.translate())
				if mrna2t.find('*')<0:
					w=w+2
					print(mrna2t)
				mrna3=mrna1[2:]
				mrna3t=str(mrna3.translate())
				if mrna3t.find('*')<0:
					w=w+3
					print(mrna3t)
			print('>'+str(seq_record.id))
			mrna1=str(seq_record.seq)
			mrna1=Seq(mrna1.replace('T','U'))
			if w==2:
				mrna1=mrna1[1:]
			if w==3:
				mrna1=mrna1[2:]
			print(mrna1.translate())

THE END
