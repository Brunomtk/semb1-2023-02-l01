# Ferramentas do toolchain

CC = arm-none-eabi-gcc
RM = rm -rf

# Diretórios arquivos objeto e de lista de dependências serão salvos

OBJDIR = build
DEPDIR = .deps

# Arquivos a serem compilados

SRCS = src/startup.c \
        src/main.c

# Flags do compilador e linker

CFLAGS = -g -mcpu=cortex-m4 -mthumb -Wall -O0
DEPFLAGS = -MMD -MP -MF $(DEPDIR)/$*.d

# Gera lista de arquivos objeto e cria diretório onde serão salvos

OBJS = $(patsubst %, $(OBJDIR)/%.o, $(basename $(SRCS)))
$(shell mkdir -p $(dir $(OBJS)) > /dev/null)

# Gera lista de arquivos de lista dependência e cria diretório onde serão salvos

DEPS = $(patsubst %, $(DEPDIR)/%.d, $(basename $(SRCS)))
$(shell mkdir -p $(dir $(DEPS)) > /dev/null)

all: $(OBJS)

$(OBJDIR)/%.o: %.c $(DEPDIR)/%.d
	$(CC) -c $(CFLAGS) $(DEPFLAGS) $< -o $@

# Cria um novo target para cada arquivo de dependência possível

$(DEPS):

# Inclui conteúdo dos arquivos de dependência

-include $(DEPS)

.PHONY: clean
clean:
	$(RM) $(OBJDIR) $(DEPDIR)
