�\�g�������t�������@�r�`�n�q�h�\

�y�@�\�z

�i�P�j�e�l�n�ǂݎ��

Argument0�@�@"GetFMO"
Argument1�@�@FMO���� �@�@�@�@�ȗ��\�i����l"Sakura"�j
Argument2�@�@��������G���g���i���j
Argument3�@�@����i���j�ȉ�Argument4,5�c�ƂÂ�

�������Ŏw�肵����������܂ރG���g���͌��ʂƂ��ĕԂ���Ȃ��Ȃ�܂�

Result�@�@�G���g����
Value[n]�@FMO�̊e�G���g�����P�G���g���PValue�ŕԂ�


�i�Q�jSAKURA API�R�[��

Argument0�@�@"SakuraAPI"
Argument1�@�@�������HWND
Argument2�@�@wparam
Argument3�@�@lparam

Result�@�@SendMessage�̌���


�i�R�jCollision�ʒu�擾�i�����ɃE�B���h�E��`�擾�j

�i���̊֐��� SAKURA API���g���� Collision�ʒu���擾���܂��j

Argument0�@�@"GetRect"
Argument1�@�@�������HWND
Argument2�@�@"head"|"face"|"bust"�@���Q

Result�@Collision�ʒu��left�i�O�Ȃ玸�s���P�j
Value0�@Collision�ʒu��left
Value1�@Collision�ʒu��top
Value2�@Collision�ʒu��right
Value3�@Collision�ʒu��bottom
Value4�@�Ώ�HWND��left
Value5�@�Ώ�HWND��top
Value6�@�Ώ�HWND��right
Value7�@�Ώ�HWND��bottom

���P�FCollision����`����Ă��Ȃ�������SSP�̈ꎞ�N���S�[�X�g��������
�@�@�@�����������肪CROW�iSAKURA API�������j�������肷��ƂO���A��݂����ł��B

���Q�F�����łR��ވȊO�̕�������w�肷��ƁASAKURA API�𓊂�����
�@�@�@Value4�`7�̂ݕԂ��܂��B�܂��A���̏ꍇ��Result��Value4�Ɠ����l�ɂȂ�܂��B
�@�@�@����𗘗p���āA�������g��HWND�𓊂��邱�Ƃɂ�莩���̈ʒu��������܂��B

��2004/7/24�ǉ��F�������HWND���E�B���h�E�Ŗ����ꍇ
�@(IsWindow�Ŏ��s�����ꍇ�j���U���g��-9999���A��܂��B
��2005/7/12�ǉ��F�������HWND�����Ŗ����ꍇ
�@(IsWindowVisible�Ŏ��s�����ꍇ�j���U���g��-9999���A��܂��B


�i�S�jDirectSSTP���M

Argument0�@�@"DSSTPSend"
Argument1�@�@�������HWND
Argument2�@�@�߂�l���v��ꍇ��"result"
Argument3�`�@SSTP�̊e�s
�i�ȉ����l�ɑ�����A���ɏ���Ȃ��A�A�����b�Z�[�W���̂�1KBytes�ȓ��ł��邱�Ɓj
��DirectSSTP��HWND�p�����[�^�͏���ɒǉ�����܂��̂Ŏw��͕s�v�ł��B

Result�@SSTP�T�[�o�̕Ԃ����s���A���M�Ɏ��s�����茋�ʂ�Ԃ���Ȃ������ꍇ��
�@�@�@�@�O���Ԃ�i���Ȃ݂ɑ��M�҂����ԁA���ʑ҂����Ԃ͂R�b�ł��j

Value0�`�@SSTP�T�[�o�̕Ԃ����e�s������A��������s�͏������܂��B
�i�����Ă��̏ꍇ�AValue0�� SSTP/1.4 200 OK �Ƃ��������U���g�R�[�h�s�A
�@���̌�Value1������ۂ̃f�[�^���i��������΁j�Ԃ锤�ł��j


�i�T�j�E�B���h�E�ړ�

Argument0�@�@"MoveWindow"
Argument1�@�@�������HWND
Argument2�@�@X���W
Argument3�@�@Y���W

Result�@�������Ԉ���Ă��Ȃ����200���Ԃ�܂��B

�i�U�j������

Argument0�@�@"Dakko"
Argument1�@�@"START"|"STOP"
Argument2�@�@��ƂȂ�HWND1
Argument3�@�@������������HWND2
Argument4�@�@X���W����
Argument5�@�@Y���W����
Argument6�@�@�Ď��Ԋu�i�~���b�j

Result�@�������Ԉ���Ă��Ȃ����200���Ԃ�܂��B

HWND1��HWND2���Ђ����܂��B�i�Ď��Ԋu�ňʒu���Ď��AHWND1�̍�����W��
�������������l�� HWND2�̍�����W�ɂ��܂��j
START���g���ƊĎ����J�n���܂��BSTART�͉���Ă�ł����܂��܂���B
STOP���g���ƊĎ����I�����܂��B
STOP���g���ꍇ��Argument2�`6�͖����Ă��܂��܂���B

�Ď�����HWND1��IsWindow�Ŗ����Ȃ����ꍇ�́AOnDakkoLost NOTIFY��
HWND2�ɑ΂��ē����܂��B�iSTOP�͂���܂���j

�y�����z

2004/05/08	Ver1.0.0	�V�K�쐬
2004/05/08	Ver1.0.1	Notify1.0�Ƀo�O���������̂ŏC��
2004/05/08	Ver1.0.3	nodummy�̍ہACROW,S-V,SSSB�̃G���g���𖳎�����悤�C��
2004/05/08	Ver1.0.4	nodummy�I�v�V�����p�~�A��������G���g���𖾎��w�肷��悤�ɂ��܂���
						�������g�̈ʒu���擾�ł���悤��GetRect�̎d�l���C�����܂����B
2004/05/16	Ver1.1.0	"Notify"�p�~�A���ėp�I��"DSSTPSend"�ǉ��B
2004/06/14	Ver1.2.0	"MoveWindow"�ǉ��B
2004/07/24	Ver1.2.1	"MoveWindow"���U���g�R�[�h�ύX�B
2004/07/25	Ver1.3.0	"Dakko"�ǉ��B
2005/05/10	Ver1.3.1	�I���������኱�������B����ň��肷��Ƃ������ǁB
2005/05/12	Ver1.3.2	"Dakko"�ŃG���o�O���Ă��̂ŏC���B"Dakko"��OnDakkoLost�ǉ��B
2005/07/12	Ver1.3.2.1	"GetFmo"�̃G���o�O���C���B"GetRect"��IsWindowVisible�ǉ��B
2005/07/26	Ver1.3.3	SSTP���M���ɗ�����ꍇ������o�O���C���BThanks to �ۂɂ��
2008/04/14	Ver1.4.1	Argument�����Ԃǂ���ɗ��Ȃ��Ă����v�Ȃ悤�ɂ����ifor KAWARI827)
2011/05/05	Ver1.4.2	"Dakko"��؍햂�_C.Ponapalt���񂪒����Ă���܂����B


�y�ӎ��z

�J���ɂ������Ă͂��т���l��gethwnd.dll�\�[�X��傢�ɎQ�l�ɂ����Ē����A
�܂�����Ȃ��炾���ԗ��p�����Ē����Ă���܂��B����\���グ�܂��B
��http://www33.tok2.com/home/ebi/index.shtml�@�����ʂ�߂�... 

�y�A����z

�A���悪�ς��܂����B
----------------------------------
���@�q�@��
----------------------------------
 ukiya@saku2.com
 http://ukiya.sakura.ne.jp/
----------------------------------
